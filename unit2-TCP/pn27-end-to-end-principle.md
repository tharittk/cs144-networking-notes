# End-to-End Principle

- why doesn't the network help ? like compress file before sending, check if the data already exists there, add security, etc.
- soruce -> C -> D -> E -> dest
- each link has a error detection: network here provides the error detection
- reasoning: if each hop checks that it is error-free, there should be no error then.
- this is wrong assumption. If D (internal) memory is corrupt (after check upon arrival) -> send to E (corrupted bit) -> E thinks it is fine too.
- this means, you must check end-to-end (at arrival and before sending out).
- for something to work correctly, it must work end-to-end. You may help in the middle (for performance improvement).
- if link layer (WiFi) tries retranmission to help improve TCP performance, this may work well but what about other link ? wire does not need that. Now things become calcified.
