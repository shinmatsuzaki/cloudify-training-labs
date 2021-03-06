# Lab: Using Scripts in Lifecycle Events

The purpose of this lab is to fix a broken blueprint and install it locally.

Ensure that the `LAB_ROOT` environment variable points to the exercise's root directory by executing:

```bash
export LAB_ROOT=~/cloudify-training-labs/using-scripts/exercise
```

### Step 1: Replace placeholders

You need to replace **_all_** the occurrences of the placeholders (“`REPLACE_WITH`”) wherever they are located under
`$LAB_ROOT`, with the suitable values and to add missing parts as well.
 
To search:

```bash
grep -r "REPLACE_WITH" $LAB_ROOT
```

### Step 2: Run in local mode

Once you're done, you can run the application in local mode:

```bash
cfy install $LAB_ROOT/blueprint/blueprint.yaml -b tomcat -d tomcat -i vm_ip_address=<your-app-VM-public-IP-address>
```

Then, run the following CLI command:

```bash
cfy deployments outputs tomcat
```

This command will display the deployment's outputs, as defined in the application's blueprint.

Browse to `http://<cli-machine-public-ip>:8081/helloworld`. The test application should show up:

![HelloWorld app](../../../raw/4.3.1/using-scripts/helloworld.png "HelloWorld app")

**NOTE**: if you use `curl` instead of a browser, you must use the `-L` flag to have `curl` follow
redirects:

```bash
curl -L http://<cli-machine-public-ip>:8081/helloworld
```

To clean up:

```bash
cfy uninstall tomcat
```
