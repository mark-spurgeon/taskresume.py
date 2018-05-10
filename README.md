taskresume.py
=======

It's a little python script that manages tasks so that when you launch a big list of things to to you can cancel and resume the process.

![tasks.png](tasks.png)

To use it, just copy the `taskresume.py` file and put it in your branch.
On your main script, load tasks like this :
```
from taskresume import TaskBundle

taskbundle = TaskBundle(slash_task=",\n") # task manager, add arguments to overwrite format

taskbundle.loadFile('tasks.txt') # load task list

if taskbundle.hasLoadedList:
    for task in taskbundle.list :
        args = task.get('args')
        status = task.get('status')
        id = task.get('id')
        #...
        taskbundle.changeStatus(id, 'error') #--> error
        #taskbundle.changeStatus(id, 'yes') --> completed
        #taskbundle.changeStatus(id, 'no') --> not completed

```
To create tasks, it's the same idea :
```
from taskresume import TaskBundle

taskbundle = TaskBundle(slash_task=",\n")

taskbundle.createFile('tasks.txt')

taskbundle.addTask({"args":["something", "some-other-thing"], "status":"no"}) #status = "no", when the task hasn't been launched

taskbundle.saveFile()

```
