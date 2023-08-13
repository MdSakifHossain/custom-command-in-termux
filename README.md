
## Steps
1. Open your Termux app.
2. Run the following command to open your shell configuration file in edit mode:
```bash
nano $PREFIX/etc/bash.bashrc
```
3. Scroll to the end of the file and add the following lines:
```bash
# Custom command to start a Python server on a specific port
function startserver() {
    if [ $# -ne 1 ]; then
        echo "Usage: startserver <port>"
    else
        python -m http.server "$1"
    fi
}

```
4. Press `Ctrl + x` then `y` to save and exit at the same time.
5. Close and reopen Termux for the changes to take effect.

Now you can use the custom command `startserver` in the terminal followed by a port number to start a Python server. For example:
```bash
startserver 8080
```

This will start a Python server on port `8080` using the `http.server` module.



---


## Explaination

In the third step, we're adding a custom function called startserver to your `Termux environment`. This function will allow you to easily start a Python server on a specific port using a single command.


Here's a breakdown of the code added in step 3:
```bash
function startserver() {
    if [ $# -ne 1 ]; then
        echo "Usage: startserver <port>"
    else
        python -m http.server "$1"
    fi
}
```

- `function startserver() {`: This line starts the definition of a new shell function named `startserver`.
- `if [ $# -ne 1 ]; then`: This line checks if the number of arguments provided when calling the `startserver` function is not equal to 1. The special variable `$#` holds the number of arguments passed to a shell script or function.
- `else`: This line starts the block of code that will execute if the condition in the `if` statement is false, meaning you've provided the correct number of arguments.
- `python -m http.server "$1"`: This line uses the Python interpreter to run the `http.server` module with the port number provided as an argument to the function. The `$1` represents the first argument passed to the function, which is the port number you want to use for the server.

So, in summary, when you call the startserver function with a port number, it checks if the correct number of arguments is provided. If yes, it starts the Python server using the specified port number. If not, it provides you with a usage message.
