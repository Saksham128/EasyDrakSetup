# VM Save-point/Snapshot creation 

Creating a save-point or snapshot is an important step for proper generating logs. VM has to retored to the previous clean state after execution of each malware executable. Restoring the VM to a fresh and clean state removes any instance of the previous executable from memory.
<br>

## VM Snapshot creation

#### 1. Parse the VM and get the VMI process list.

- Create the VM
  ```bash
  sudo xl create /etc/xen/win7.cfg
  ```
- Wait for some time to let windows boot and then get process list
  ```bash
  sudo vmi-process-list windows7-sp1
  ```

  <img title="Parsing and VMI process list" alt="Parsing and VMI process list" src="/Installation_instructions/images/vmipsl.png" width="500" height="600">

#### 2. Change directory to the folder where you want to store the snapshot file

- In our case we are storing the snapshot.sav file to the drakvuf folder.

  ```bash
  cd ~/drakvuf
  ```
#### 3. Using xen command make a snapshot file of the VM

- Make sure you have made all the necessary changes to your VM before executing this command. Try to avoid "xl create" command after this as we have faced system corruption issue.

  ```bash
  sudo xl save <domain-id> <snapshot-file-name> <vm's/config/file/loacation> 
  ```

  For example:
  ```bash
  sudo xl save 1 snapshot.sav /etc/xen/win7.cfg
  ```
  In this, <br>
  1 = Domain ID of the VM. <br>
  snapshot.sav = Name of the save file. <br>
  /etc/xen/win7.cfg = Absolute path of VM's configuration file. <br>
  
  <img title="Snapshot creation" alt="Snapshot creation" src="/Installation_instructions/images/vmSave.png" width="650" height="500">
