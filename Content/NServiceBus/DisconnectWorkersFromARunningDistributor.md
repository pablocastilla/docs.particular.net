---
title: Disconnect Workers from a Running Distributor
summary: How a worker can be disconnected from its distributor using powershell
tags: 
- Scalability
- Distributor
---



The NServiceBus Distributor sends messages to a worker after the worker sends a register message to it, this message contains a SessionID that identifies the current relation with the distributor and also the capacity of the worker. This way the distributor has a ready message in its storage queue for every message a worker can receive, and also it keeps in memory a list of workers with its session.

##How a worker can be disconnected?
If the worker is configured using the NServiceBus.Distributor.MSMQ NuGet there is a PowerShell functionallity that can be use to remove a Worker from a Distributor. The steps are the following:

1. Load the [NServiceBus PowerShell CmdLet](managing-nservicebus-using-powershell.md) and execute Remove-NServiceBusMSMQWorker WorkerAddress DistributorAddress.
<p class="alert alert-info">
  NOTE: 
   * The WorkerAddress = the worker queue name, eg Worker@localhost
   * The DistributorAddress = the distributor queue name eg MyDistributor@localhost, Note: you just pass the distributor queue name, the PS script automatically appends ".distributor.control" to the end of the distributor queue.
</p> 


2. Wait for worker to drain all queued messages in its input queue.
3. Shutdown the endpoint.



##What's happening inside the distributor after the PowerShell is executed?
1. An unregister message is sent by the PowerShell to the distributor control queue.
2. When the distributor processes it the worker with the address specified in the message is set with SessionID  "disconnected".
3. Ready messages sent back by the worker to the distributor never match the session, so they are skipped and that way the worker won't receive any message more from the distributor.



