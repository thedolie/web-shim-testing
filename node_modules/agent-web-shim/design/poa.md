Agent Shim

Brainstorm
Current state of this PoA
Possible states
brainstorm:  still in infancy; major changes likely
draft: getting reviewed; changes likely
approved: only anticipate minor changes
changes accompanied by a call-out-comment
typos don't need comment

Joe Genereux
Responsible

In brief
In order for an edge agent to communicate with any other agent via a wire message, the edge agent requires the functionality to be able to pack (prepare) and unpack (read) agent messages and to deterministically, and safely handle them. The Agent Shim is geared toward light-weight pack and unpack functionality, in a javascript environment, following the Agent Message Encryption Serialization (AMES) standard. This POA outlines the common functions, handlers, and tests that will be required to properly develop the Agent Shim to perform as outlined.
Setting the stage - The Javascript Developer
10 years ago javascript was a very limited and fairly small ecosystem with developers using it for very limited web based functionality that barely extended beyond functionality to change text on a button click on a web page. Today we paint a very different picture. Javascript is everywhere. Advances in framework technology, due mostly to big organizations developing larger and larger web applications, exploded the javascript ecosystem, and now you will see JS running not only on the browser, but on native mobile applications, servers, and even desktop applications. As such we have seen a vibrant and vast community of developers emerge that work every day in the JS environment all over technology stacks.  These developers have a wide range of skill sets and many very different backgrounds, which can be seen in the variety of open source libraries available on the Node Package Manager (npm). 

The Agent-to-Agent protocol outlined in the hyperledger/indy-hype repo sets a standard that allows communication between agents in a brand new paradigm that most of the JS ecosystem is not used to. As such one of the main goals of this POA is to understand the JS developer (JSD) and provide a package that is easy for that developer to consume and understand.

Goals/Requirements

Lightweight. The entire agent shim needs to easily be transported to the edge agent upon api request
Abstract. The JSD will not fully comprehend what is going on under the hood with wire messages, and one of the primary focuses of this library is to make it easy to consume, and while we anticipate a learning curve, making it as reasonable as possible to understand is an obvious requirement.
Performant. This library needs to perform its pack and unpack functionality at a very rapid rate in order to provide reasonably timed delivery of data.
Documented. Being an open source npm package the JSD needs to have clear documentation about how to approach a new paradigm in transport and packaging of data. 
Easy to integrate into an existing ecosystem. While some changes of architecture may be required, making it easier for the developer to integrate into their codebase, or to design around from the ground up is key. 
Public Methods
shim_pack(): Prepares the agent message for the JSD. Once successfully packed the JSD is prepared to send the message over the protocol (the wire) defined by the endpoint the developer is communicating with. 

shim_unpack(): Retrieves the agent message from a wire message sent to the JSD and the potential provenance of the message.
Agent Shim Flow

Assuming the JSD is requiring this package from the NPM repo, we can assume the flow will loosely follow this example for the JSD. A key part of this is ensuring the developer does not step too far from their normal approach to api integration.

JSD requires the npm module for the agent-shim. 
JSD prepares the message he would like to send to the agent he is targeting.
JSD uses the shim_pack() method to encrypt and prepare the message using the AMES format.
JSD uses the transport layer (http, zmq, etc.) to send the message to the agent.
Agent receives the message
Agent uses the shim_unpack() method to extract the message and 


__Other_sections__
See Also


