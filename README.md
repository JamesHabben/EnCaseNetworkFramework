#Scripts using the Framework
|Script|Description|
|---|---|
|**Sysinternals Eula Scan**|Scan a network for the existance of eula registry keys indicating usage of a Sysinternals tool on each node.  Output is currently in the console tab and lists each tool that has the EulaAccepted value name in NTUSER.DAT\\Software\\Sysinternals subkeys.|
#EnCaseNetworkFramework
This is a framework written in EnScript to utilize the network capabilities of EnCase.  The purpose is to allow for someone to build a quick network enabled EnScript to respond quickly to threats with minimal code being written.  

The framework has a built-in GUI that prompts the user for the network mode and the network nodes to scan.  This GUI can be modified to request more specific information from the user.

#Network modes
|Mode|Description|
|----|----|
|**Enterprise** |Utilize the EnCase Enterprise SAFE infrastructure to scan a full network|
|**Direct**     |Contact individual nodes using the Direct Servlet function of EnCase Forensic|
|**Local**      |Scan the local machine that EnCase is installed on (mostly for debugging and testing)|
  
#Demo Code
This code will first prompt the user for the network mode and hosts to scan.  Then it will list the physical and logical drives that are attached to the remote node(s).
```c++
include "EncaseNetworkFrameworkLib"

class MyNetClass : NetworkFrameworkClass {
  MyNetClass () :
    super("Demo Class"),
    HelpText("This is some example text to explain the usage when the user clicks the help button")
  {
  }
  
  virtual void ScanNode (ConnectionClass con, SnapshotClass snap, DeviceInfoClass devList) {
    Console.WriteLine("Host: {0}", con.Name());
    foreach (DeviceInfoClass di in devList) {
      Console.WriteLine("  {0}: {1}", di.IsPhysical() ? "Physical" : "Logical", di.Name());
    }
  }
}

class MainClass {
  void Main() {
    MyNetClass nf();
    nf.ShowDialog();
    nf.RunScan();
  }
}
```
#Output to Console
```
Host: Local Machine
  Logical: C
  Physical: 0
```
#Screen Shots of Standard Dialog
<img src="http://i.imgur.com/PmZwJm4.png" title="source: imgur.com" />

<img src="http://i.imgur.com/XOy38TV.png" title="source: imgur.com" />
