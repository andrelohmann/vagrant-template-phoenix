# vagrant-template-phoenix
create a vagrant machine with local domain and ansible deployment to install all necessary tools, to start phoenix development

phoenixframework (http://www.phoenixframework.org/) is a elixir mvc framework, to write modern applications in the elixir language

1. clone this project
2. customize Vagrantfile
3. customize ansible/playbook.yaml
4. run

```
vagrant box update
vagrant up
```

after you have joined the machine with ** vagrant ssh **, run the following commands, to install the phoenix framework and create your first project

```
cd Workspace
mix local.hex
mix archive.install https://github.com/phoenixframework/archives/raw/master/phoenix_new.ez
mix phoenix.new hello
```

now edit the last lines of hello/config/dev.esx to the following content
```
# Configure your database
config :hello, Hello.Repo,
  adapter: Ecto.Adapters.Postgres,
  username: "vagrant",
  password: "vagrant",
  database: "vagrant",
  hostname: "localhost",
  pool_size: 10
```

now you can run your application

```
cd hello
mix ecto.create
mix phoenix.server
```
