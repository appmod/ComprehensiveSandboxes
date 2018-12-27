# Towards Mining Comprehensive Android Sandboxes [[pdf](paper/ICECCS.pdf)] [[slides](paper/ICECCS.pptx)]

## Dataset 
The Android Apps used in the evaluation are 25 pairs of real benign and malicious apps from [Androzoo](https://androzoo.uni.lu/), please refer to the app list in the [file](selected_apps.txt)

## Building Sandboxes
- We leverage an automated test case generation tool, named [Droidbot](https://github.com/honeynet/droidbot), to generate a rich set of GUI test cases for exploring behaviors of the app. 

- During the execution of these test cases, we record the API calls with input parameter values by [Droidmon](https://github.com/appmod/droidmon). Our approach analyzes four different types of APIs: sensitive, reflection,
BroadcastReceiver, and SharedPreferences APIs. Please refer to the log diff in the folder [sep_diff](sep_diff) and [sep_ui_diff](sep_ui_diff)

- We leverage the collected parameter values, and the list of requested permissions to create a sandbox that can protect users from malicious behaviors. 

## Evaluation
- Two baselines: 
1. BoxmateA considers execution of sensitive APIs in benign apps to construct sandboxes [[script](pyscripts/permission_based_sandbox.py)]. 
2. BoxmateE additionally takes into account GUI elements that call sensitive APIs when inferring sandboxes [[script](pyscripts/baseline_2nd.py)].

- Our approach [[script](pyscripts/proposed_approach.py)]
