# Interactive View

Modern frameworks and technologies allow splitting the frontend and backend completely, transforming the view into an interactive client which handles all communication with the server.

## Architecture

This mixes well with client-server architectures.

## State

Data such as results from requests, or the user information, can be stored locally by the frontend client, which now handles part or the totallity of the application state.

## Example

A Spring MVC application offers REST web services. The client is a REACT with Redux client. Both the backend and frontend can be in different servers.

## Advantages

- Easier to generate interactive views
- Changing view does not require reloading
- Local context and data storage
- Frontend and backend dissociated

## Disadvantages

- Heavy frontend
- Requires more knowledge
- Sessions are harder to handle
