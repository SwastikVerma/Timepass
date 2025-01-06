INSERT INTO Attendees (AttendeeID, FirstName, LastName, Email, Phone)
VALUES 
    (1, 'John', 'Doe', 'john.doe@example.com', '1234567890'),
    (2, 'Jane', 'Smith', 'jane.smith@example.com', '9876543210'),
    (3, 'Alice', 'Brown', 'alice.brown@example.com', '5556667777');


INSERT INTO Organizers (OrganizerID, OrganizerName, Email, Phone)
VALUES 
    (1, 'Global Events Inc.', 'contact@globalevents.com', '1112223333'),
    (2, 'Elite Planners', 'info@eliteplanners.com', '4445556666');

INSERT INTO Venues (VenueID, VenueName, VenueAddress, VenueCapacity, VenueAvailability)
VALUES 
    (1, 'Grand Hall', '123 Main Street, Cityville', 500, 'Available'),
    (2, 'Conference Center', '456 Elm Street, Townsville', 300, 'Booked'),
    (3, 'Open-Air Arena', '789 Park Avenue, Metropolis', 1000, 'Available');

INSERT INTO Events (EventID, EventName, EventDate, VenueID, OrganizerID)
VALUES 
    (1, 'Tech Conference 2025', '2025-02-15 10:00:00', 2, 1),
    (2, 'Music Festival', '2025-03-20 18:00:00', 3, 2),
    (3, 'Charity Gala', '2025-04-05 19:00:00', 1, 1);

INSERT INTO Tickets (TicketID, TicketPrice, AttendeeID, EventID)
VALUES 
    (1, 99.99, 1, 1),
    (2, 49.99, 2, 2),
    (3, 199.99, 3, 3),
    (4, 149.99, 1, 2),
    (5, 79.99, 2, 1);

SELECT * FROM Attendees;
SELECT * FROM Organizers;
SELECT * FROM Venues;
SELECT * FROM Events;
SELECT * FROM Tickets;
