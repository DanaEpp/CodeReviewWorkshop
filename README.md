# "The Art of Finding Security Vulnerabilities in Code" Workshop Materials

All students taking my workshop should install the following tools:

- [dotnet](https://dotnet.microsoft.com/en-us/download/dotnet/6.0)
- [jd-cli](https://github.com/intoolswetrust/jd-cli)
- [ilspycmd](https://github.com/icsharpcode/ILSpy/releases) (Get v8.2)
- [highlight](https://gitlab.com/saalen/highlight)
- [graudit](https://github.com/wireghoul/graudit)
- [semgrep](https://semgrep.dev/docs/getting-started/quickstart)

For students wishing to participate in the labs to exploit code, you should also install docker:
- [Docker desktop](https://www.docker.com/products/docker-desktop/)
- [docker-compose](https://github.com/docker/compose)

## Setting up jd-cli
Consider making a script and dropping it in **/usr/local/bin/jd-cli**:
```sh
#!/bin/sh

java -jar "/opt/jd/jd-cli.jar" $@
```
Don't forget to make it executable (`chmod 755 /usr/local/bin/jd-cli`).

## Setting up ilspycmd
Consider linking ilspycmd in **/usr/local/bin/ilspycmd**:
```sh
ln -s /opt/ILSpy/ICSharpCode.ILSpyCmd/bin/Debug/net6.0/publish/ilspycmd /usr/local/bin/ilspycmd
```

## Setting up graudit
```sh
cd /opt
git clone https://github.com/wireghoul/graudit

# Change to ~/.zshrc if on macOS and using zsh
echo 'PATH="$HOME/graudit:${PATH:+:${PATH}}"; export PATH;' >> ~/.bashrc

# Add this in your .bashrc or .zshrc
export GRDIR=/opt/graudit/signatures
```

## Setting up semgrep
On a Mac, use `brew install semgrep`.

On Linux or Windows, use `python3 -m pip install semgrep`

Once installed, get your [CLI app token](https://semgrep.dev/orgs/-/settings/tokens/cli) from your free account on semgrep and login to the CLI with the following cmd:
`SEMGREP_APP_TOKEN=<token> semgrep login`

## Setting up live vulnerable target for last labs
To complete the final labs, you will need to have docker and docker-compose installed.

Then you can launch the environment with the following:
```sh
git clone https://github.com/snoopysecurity/dvws-node.git
cd dvws-node
docker-compose up
```

