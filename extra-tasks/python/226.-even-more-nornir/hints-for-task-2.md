# Hints for Task 2

Change all lines referring to "net\_connect". That will be in each of the 4 functions

1.  show\_ap\_summary()

    Change:

    ```python
    print(net_connect.send_command("show ap summary"))
    ```

    To:&#x20;

    ```python
    results = nr.run(
        task=netmiko_send_command,
        command_string="show ap summary"
    )
    print_result(results)
    ```
2.  show\_client\_summary()

    Do the same changes as in previous  function
3.  show\_cdp\_neighbors()

    Do the same changes as in previous functions
4. save\_config\_to\_file()
   1. In the existing script, we saved the output from netmiko to "output". Change this to the same format as the previous functions, saving the results in "results". Exactly the same as the previous functions. We are now ready to save the results to a file
   2.  The results object is actually an object of type "AggregatedResult", containing results for each object that tasks has been run on, as a "MultiResult" object. Each MultiResult object is accessed by the name of the host. So for our example host file you would have two MultiResult objects

       ```python
       results['your_wlc']       # Object of type MultiResult
       results['shared_wlc']     # Object of type MultiResult
       ```
   3.  Each of these contains a list with the results of each task run on that object, starting from 0. So with one task run for the "your\_wlc" host, the output (e.g. the "show run") will be stored in:

       ```python
       results['your_wlc'][0]  # Output of the first task. Use str() to change to text
       ```
   4.  This object will also have a status (boolean value) telling if the task failed. We will use this to only save the run-config if the command has NOT failed. Failed tasks can be if login failed, host unreachable, etc.

       ```python
       results['your_wlc'][0].failed           # Boolean value, True or False
       ```
   5. So, the rest of the function can be something like this:

```python
    for host in nr.inventory.hosts:              # Loop over all hosts in the Nornir inventory
        if results[host][0].failed:              # Check if the first task have status failed, if failed print an error message
            print(f'Save run-config for {host} ({nr.inventory.hosts[host].hostname}) failed. See nornir.log for details.')
        else:                                    # Else (if the task is NOT failed), run the file writing part
            now = datetime.datetime.now()        # Get the current timestamp
            filename = f"{nr.inventory.hosts[host].hostname}-run-conf ({now.strftime('%Y-%m-%d %H:%M:%S')}).txt" # Make a filename
            with open(filename, 'w') as f:       # Write the actual file
                f.write(str(results[host][0]))
            print(f"Config saved to {filename}")
```

Reference and more info: [https://nornir.readthedocs.io/en/latest/tutorials/intro/task\_results.html](https://nornir.readthedocs.io/en/v2.5.0/tutorials/intro/task_results.html)
