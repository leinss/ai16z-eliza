# Run the Eliza React Chat Client w/ Agent

https://app.dework.xyz/godsdotfun/integrations-91104?taskId=809403c5-e7ed-4256-aa28-a96415f792e9

## Description

Spin up an instance of the React Chat Client w an agent and get the agent conversing with the user in a local development environment.We need to get Eliza agents connecting to this React Chat client:https://github.com/elizaOS/eliza/tree/develop/client- We need to be connect an eliza agent instance with the React Chat Client from the ElizaOS repo- The agent should need to connect using a oauth api key- Agent should be able to send images and text- The React chat client app needs to be hosted on Vercel, Railway or Digital Ocean- Documentation on the workflow; and the technical steps we need server side to generate the oauth keys

## Comments

The client ui calls the client-direct rest api, this task will need to add features in both packages.The flow would roughly be:

dev authenticates to the client ui by SOL wallet

dev manages his agents (create, setup api token, specify agent client-direct deployment url for the ui to know where to talk to the agent) on a separate page

dev uses this token then for his own agent deployment (maybe by specifying pairs of origin (the deployed client ui domain) and the related api key)

then the user of the client ui should be shown in the left panel all created agents and the ui sends the api token along with each request which the client-direct package of the agent verifies.

## Done

- simple solana wallet integration
- api key generation on `client`
    - currently in localStorage:
      [{"name":"test","origin":"https://ai16z-eliza.vercel.app","apiKey":"6b31db7b-76be-4a94-a2ff-1d5e3802a609"}]
- `client uses api-keys for requests made to backend
    - `/agents`
    - `/agents/:agentId`
    - `/:agentId/message`
    - `/:agentId/tts`
    - `/:agentId/whisper`
  - new search params with origin
- `client-direct` uses api-keys for requests made to backend if not coming from same origin
- client deploy

## TBD


- separation of agent api-key and ui user api-key
- one room creation per agent
