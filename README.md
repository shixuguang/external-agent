# deploy wxo adk external-agent to BYOA

```
  curl -kLo ./cpd-cli-workspace/olm-utils-workspace/work/app-proxy-config.yaml https://raw.githubusercontent.com/shixuguang/external-agent/refs/heads/main/app-proxy-config.yaml

  cpd-cli manage create-gitapp-application --cpd_instance_ns=zen \
    --app_name=external-agent \
    --app_port=8080 \
    --repo_url=https://github.com/shixuguang/watsonx-orchestrate-developer-toolkit.git \
    --repo_branch=main \
    --repo_app_dir=external_agent/examples/langgraph_python \
    --app_envs='[{"name":"WATSONX_SPACE_ID","value":"your ibm cloud space_id"},{"name":"WATSONX_API_KEY","value":"your ibm cloud api key"}]' \
    --app_proxy_config_yaml='/tmp/work/app-proxy-config.yaml' \
    --cpu=400m \
    --memory=200Mi \
    --cpu_limit=500m \
    --memory_limit=400Mi
```

#### application available at `https://zen-route/physical_location/default-pl/<app_name-app_run_id>/docs/`

To `try it out`, use this `request body`:  
```
{
  "model": "ibm/granite-3-3-8b-instruct",
  "context": {},
  "messages": [
    {
      "role": "assistant",
      "content": "how to use foundational models?"
    }
  ],
  "stream": false
}
```
