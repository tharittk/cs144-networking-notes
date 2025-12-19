# Finite State Machine

- transition cannot be ambiguous
- example: http request
- idle (viewing) -> page requesting (event = load new page, action = open connection)
- <-, event = connection close, finish request, action = close connection
- another state: request pending
- TCP is also modeled as FSM
- Tearing down connection (after syscall close())
- ESTABLISHED -> FIN WANT 1 --- active closer: who starts the process, CLOSE WAIT --- passive closer: who responds
- if the active closer decides to send FIN, it can no more send data (by definition)
- the passive closer can still send some data left (it sends the ACK to the active closer, ac moves to FIN WAIT 2)