> [!NOTE]
> This repository was archived because the little functional use wasn't worth the administration overhead.  
> We removed the callback app in our 3CX installation and the server automatically replaces this app with "End Call" in the forwarding rules. "End call" aligns with our default policy; ending the call after ~20 seconds of not picking up a ringing phone.

# 3CX Callflow app; CALLBACK

Call flow app for monitoring extensions and linking them both when they become available.

WARNING; This application is not robustly handling concurrent calls!

## Installation

1. Build the project with the Call Flow Designer application
1. Upload the zip file to your 3CX server

## Configuration

The project builds with an extension number attached! You can use this extension within your call routing.

1. Setup Forwarding rules to forward to your Call Flow App
    1. Choose "Forward to number"
    1. Fill in the extension number of your Call Flow App
    1. The above should work as if you forward to internal extension

## Error handling

The call flow app will send an alert to the e-mail address registered as ```PBXERRORMAIL```.
Update this e-mail address within your 3CX dashboard, or find the parameter at Settings/Parameters/Custom (only superuser has access to this option).

## Audio generation

Generate your own audio, Google Text-To-Speech has a one-shot demo tool you can use.

### Intro

```ssml
<speak>
  User is not available at this moment. <break strength="weak"/>
  To activate automated callback <break strength="medium"/>
  <emphasis level="high">Press 1</emphasis>
</speak>
```

### Callback verification

```ssml
<speak>
  <emphasis level="high">ok</emphasis> <break strength="weak"/>
  I'll call you when this user becomes available.
</speak>
```
