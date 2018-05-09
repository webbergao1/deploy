# deployment
Deploys some of nodes with the docker-compose.

We used two docker images.\<br> 
## go-seele:
    The seele node image is used to start the node and client.\<br> 
    * Command:
        ```makefile\<br> 
        node start -c <configfile>
        ```
    * With docker: \<br> 
        ```makefile
        docker run -v <local config path>:/go-seele/config -it go-seele node start -c /go-seele/config/<configfile>
        ```

## Monitor-api:
    The monitor-api image is used to start an service to linked on an node.
    The service gets some informations form the node, and send them to another server which used to collect and analysis the informations.
    Each node corresponds to an monitor-api.\<br> 
    Start with docker:
        ```makefile
        docker run -v <configfile>:/monitor-api/app.conf monitor-api
        ```

# configuration folder
[node_config] 
Puts node configuration files

[monitor_api_config]
Puts monitor-api configuration files

# docker-compose.yml
Start 2 nodes and 2 monitor-api services with docker images.

# docker-compose-monitor.yml
Start 2 nodes and 2 monitor-api services with docker images.
Same with docker-compose.yml.

# docker-compose-node.yml
Start 2 nodes with docker image, no monitor-api services.

# docker-compose-build-monitor.yml
Start 2 nodes and 2 monitor-api serviecs with source code.\<br> 
Source code must be put in 'github.com/seeleteam/go-seele' and 'github.com/seeleteam/monitor-api'.\<br> 
And the deployment project must in 'github.com/seeleteam/deployment'.\<br> 

# docker-compose-build-node.yml
Start 2 nodes with source code.
Source code must be put in 'github.com/seeleteam/go-seele'.\<br> 
And the deployment project must in 'github.com/seeleteam/deployment'.\<br> 

# See the yml file for more details.