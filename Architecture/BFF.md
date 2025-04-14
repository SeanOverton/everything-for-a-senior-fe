# BFF
The backend-for-frontend concept is a seemingly opinionated architecture design that decouples the typical frontend (client) and backend (server) systems.

Different engineering teams have different ideas about the role of the BFF but generally the need for the BFF came about not long after the explosion of microservice architecturess. With the increase in microservices there was an increasing, amount of endpoints that the client (usually frontend website such as an single page app (SPA)) has to make requests to. As most microservices also are responsible for a specific isolated domain with respective databases they not always offered data in the way the frontend client required. This could result in the client doing expensive computation work after making multiple requests to microservices which was not ideal. This resulted in complex API interactions for the client (many requests) as well as no place for the frontend team to do data transformation/preparation work required for the client software. The individual microservice teams push back on requirements of the frontend team because "its not there job" which might be quite justified. On top of this, each client type has different needs for data. This could result in the server teams implementing specific endpoints, for client 1 (mobile device) and then again for the web app. The BFF is meant to serve as the layer of abstraction to decouple the domain specific server from the client specific needs.

## The solution?
The backend-for-frontend is actually just another server that sits as a proxy between the frontend client and the backend microservices. Some key attributes:
- the client team is responsible for this server
- data transformation work, unique to the specific client type, should be implemented on the BFF
- a BFF can/should exist for each client type such as mobile app and traditional web app client, while the BFF's share the same microservices
- the BFF can also simplify the requests on the frontend client side. For example, reducing 3 sequential requests into 1 request to the BFF which in turn would do the 3 requests to the multiple microservices and combine the response into something digetible for the client. This may have network improvements given the BFF should be on the same network on the infrastructure as opposed to where the client is.

## Summary
The BFF is an important part of solution design for the frontend engineer.
