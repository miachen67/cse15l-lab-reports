# Lab 3 Report <br/>
In this week's lab, we started our own servers!

## ChatServer Code
![Image](lab3code1.png)

## Screenshot 1
![Image](ss1forlab3.png)

- When we add the query `/add-message?s=Hello&user=jpolitz` to our url, the handleRequest method is called.
- The `handleRequest` method takes in the url as an argument. Additionally, our `ChatServer` class has a field `String x` that is updated each time a message is added successfully.
- The field `String x` was changed since the message "jpolitz: Hello" was added to it. Also, the `URI url` argument was also updated to add the query `/add-message?s=Hello&user=jpolitz`.

## Screenshot 2
![Image](ss2forlab3.png)
- When we add the query `/add-message?s=hi there&user=mia` to our url, the handleRequest method is called.
- Similar to the first screenshot, the `handleRequest` method takes in the url as an argument. Additionally, our `ChatServer` class has a field `String x` that is updated each time a message is added successfully.
- The field `String x` was changed since the message "mia: hi there" was added to it. It now consists of the two messages with a `"\n"` in front.  Also, the `URI url` argument was also updated to add the query `/add-message?s=hi there&user=mia`.

## SSH
![Image](ss3forlab3.png)
- The private key is the one without the `.pub` ending, which would be `/home/.ssh/id_ed25519`.
- The path to the public key is `/home/.ssh/id_ed25519.pub`.

![Image](ss4forlab3.png)
- This is my terminal reaction that didn't require me to log in!

