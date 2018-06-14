# github-auto-pull
Automagically pull and restart your program whenever git changes are made.

## Usage
Download an executable for your platform from [the releases page](https://github.com/programmer5000-com/github-auto-pull/releases).
Then create the script you want to run:

```bash
echo "echo test" > script.sh
chmod +x script.sh
./github-auto-pull script.sh
```

If you get an EACCES error, try this:

```bash
sudo apt-get install libcap2-bin
sudo setcap cap_net_bind_service=+ep `readlink -f \`which node\``
```

github-auto-pull binds on port 80, which can usually only be bound by root. These commands allow node to bind on port 80. See also [this StackOverflow post](https://stackoverflow.com/a/23281417/6560716).

Otherwise, stop github-auto-pull.

Then go into your desired github repo. Create a webhook, setting your IP address as the URL. Make sure to set the content type to `application/json`. Then generate a random string and set that as your secret for the webhook.

```bash
./github-auto-pull script.sh INSERT_SECRET_HERE
```

Save the webhook and your console should tell you that you got a ping.
