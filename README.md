# Logger

## 1. Introduction
Task offloading application often need to offload the task at a particular point of time. Thus, we need to find an optimal computational
node to offload the task at that time. Estimating the usage statistics of the available computational nodes at a particular time in near
future can help to determine the optimal computational node.

## 2. What does the app do?
Every 15 minutes, this app logs following paramters with a timestamp,
1. available batery%, 
2. RAM usage percentage
3. CPU frequency
4. available internal storage (in KB) )

The values are written to a ```.csv``` file with the aim to create a dataset. This dataset will be used to predict the system paramters 
of the phone at a particular time. Even if the user switches off the phone  (or battery runs out) the app will start logging again when
the phone is turned on again. The user can explicitly stop background logging from the app.

Google Work Manager API has been used to handle the periodic background work of logging.

## 3. Win the user trust
This app does not do any network activity which means the app does not send the data to any server. The log file is stored on the external
emulated storage of the app folder. It makes the log file visible to the user so that the user can be confident about the data that is being
logged.

No indivduality or unique identifier of the device or of the user is stored in the log file or within the app. 

## 4. Limitation
The logging work runs in background every 15 minutes. Since, different OEMs implement their own battery optimizers, they tend to
aggressively kill the background tasks. [Click here)(https://dontkillmyapp.com) to know more on this. As a workaround, the app should be
exempted from battery restrictions manually.

## 5. Improvements/Future Work
Currently, the future prediction of system paramters is being done in separate project on an experimental basis. We can try doing this
prediction within the app itself.
