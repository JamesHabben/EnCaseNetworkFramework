EnCaseNetworkFramework
======================
This is a framework written in EnScript to utilize the network capabilities of EnCase.  The purpose is to allow for someone to build a quick network enabled EnScript to respond quickly to threats with minimal code being written.  

The framework has a built-in GUI that prompts the user for the network mode and the network nodes to scan.  This GUI can be modified to request more specific information from the user.

#Network modes:
|Mode|Description|
|----|----|
|**Enterprise** |Utilize the EnCase Enterprise SAFE infrastructure to scan a full network|
|**Direct**     |Contact individual nodes using the Direct Servlet function of EnCase Forensic|
|**Local**      |Scan the local machine that EnCase is installed on (mostly for debugging and testing)|
  
#Usage
