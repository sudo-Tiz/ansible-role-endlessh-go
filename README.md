# Endlessh Ansible Role
**WIP Roles waiting for changes in endlessh-go. DO NOT USE**  
[endlessh-go](https://github.com/shizunge/endlessh-go) is a golang implementation of endlessh, a ssh trapit
- with everything run in [Docker](https://www.docker.com/) containers
- powered by [endlessh-go container image](https://hub.docker.com/r/shizunge/endlessh-go)


## Installing

To configure and install endlessh on your own server(s), you should use a playbook like [Mother of all self-hosting](https://github.com/mother-of-all-self-hosting/mash-playbook) or write your own.

## Configuration

To enable this service, add the following configuration to your `vars.yml` file and re-run the [installation](../installing.md) process:

```yaml
########################################################################
#                                                                      #
# endlessh                                                                 #
#                                                                      #
########################################################################

endlessh_enabled: true

# config
intervalMs: 1000
bannerMaxLength: 32
maxClients: 4096
connType: "tcp"
connHost: "0.0.0.0"
connPorts: []
prometheusEnabled: false
prometheusHost: "0.0.0.0"
prometheusPort: "2112"
prometheusEntry: "metrics"
prometheusCleanUnseenSeconds: 0
geoipSupplier: "off"
maxMindDbFileName: ""

########################################################################
#                                                                      #
# /endlessh                                                                #
#                                                                      #
########################################################################
```

### Exposing the web interface

By setting a hostname you will expose endlessh on this domain.
Usually you should also set up basic_auth in this case, otherwise everyone will be able to access your metrics

```yaml
endlessh_hostname: endlessh.example.org

# Uncomment following lines to add basic auth
#endlessh_container_labels_metrics_middleware_basic_auth_enabled: true
#endlessh_container_labels_metrics_middleware_basic_auth_users : '<user>:<hashed_password>'

```
