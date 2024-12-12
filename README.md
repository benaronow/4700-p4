# 4700-p4
### High Level Approach
1. Parse arguments for host and port for Sender and Receiver
2. Create Sender and Receiver given host and ports
3. Establish UDP connection with sender and receiver
4. Run Sender and Receiver
5. The Sender will:
    - Send messages
        - Receives acknowledgments that have been sent,
        - Retransmits when messages drop
        - Exits when no packets are currently in flight and no data is left to send.
6. The Receiver will:
     - Continuously listen, with select, for incoming messages on the UDP socket.
        - When a message is received, it processes the message by checking 
          if it is a 'done' signal or a regular message
            - If it is a 'done' 
                it prints out the received data and sends a confirmation. 
            - else
                it appends them to the received list if not duplicates
                and sends an acknowledgment back to the sender.
        - Detects dropped messages
    

### Challenges
- Performance for dropped packets and retransmitting

### Testing
This code was tested using the given configurations.