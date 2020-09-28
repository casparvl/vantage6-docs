---
description: >-
  The server manages users, organizations, collaborations, tasks and results. In
  this section we will explain how to configure and manage a server.
---

# Running the server

## 🆕 \(Re-\)Configuring a \(New\) Server

After installing the necessary elements, we need to create and configure a server.

Servers are created from a configuration file. This file can be generated through the command `vserver new`or manually from a YAML file manually, as explained [in this section](server-configuration.md).

## 📥 Importing entities

After configuring the server, we need to define the users, organizations, collaborations, etc. This can be done using the `vserver import` command, as explained [in this section](importing-entities.md).

Notice that we need to follow the same steps when loading/importing new data.

## 🏤 Managing Server Data

Managing entities at the server \(e.g. users, organizations, etc...\) is usually done through the RESTful API. As administrator you also have access to a Python API by using the command `vserver shell` which opens an iPython shell in which all database models are available. To see what you can do with these models, see [this](shell.md) page!

## 🏎 Starting the server

Once the configuration is done and you created at least one user, you can start the server instance by using `vserver start` and then selecting the configuration you want to use.  If you know the name of the configuration, you can use the flag `--name` to specify it. 

If you have a configuration file which is in a non-default location than you can specify this by the `--config` flag. 

{% hint style="info" %}
Note that having Docker installed is **not** strictly  necessary to run the server. However, it is needed if you want to run a private registry on the same machine. See [Docker registry](../../installation/docker-registry.md) for details.
{% endhint %}

## 🧁 Deployment of a Production environment

We give some recommendations for deploying a vantage6 server in [this](deployment.md) section.

## ✍ Logging

If logging to the console is enabled, starting the server or loading the fixtures should output some information that can be helpful in determining the cause of problems. For example, the output below shows:

* Which environment was used
* What configuration file was used
* Which database was used

```bash
################################################################################
#                              vantage6                                        #
################################################################################
Started application 'vantage6' with environment 'test'
Current working directory is '/home/test-user'
Succesfully loaded configuration from '/home/test-user/.config/vantage6/server/default.yaml'
Logging to '/home/test-user/.cache/vantage6/log/server/default.log'
Initializing the database
  driver:   sqlite
  host:     None
  port:     None
  database: /home/test-user/.local/share/vantage6/server/default/test.sqlite
  username: None
Database initialized!
```

## 💻 Server Commands

As a reference, these are the sub-commands available to manage the server\(s\). These commands can also be found by simply calling `vserver` .

| Command | Description |
| :--- | :--- |
| `vserver attach` | Attach the logs from the Docker container to the terminal |
| `vserver files` | List the file locations of the server instance |
| `vserver import` | Import server entities as a batch |
| `vserver list` | List the available server instances |
| `vserver new` | Create a new server configuration |
| `vserver shell` | Run a server instance python shell |
| `vserver start` | Start the server |
| `vserver stop` | Stop a or all running server |

Alright. After having the server up and running, we need to configure the nodes.
