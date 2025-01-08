CREATE TRIGGER AfterStudentInsert
ON Student
AFTER INSERT
AS
BEGIN
    DECLARE @StudentID INT;
    DECLARE @FullName NVARCHAR(150);
    DECLARE @Branch NVARCHAR(50);
    DECLARE @Marks INT;
    DECLARE @Location NVARCHAR(255);

    -- Iterate through inserted rows
    DECLARE cur CURSOR FOR
        SELECT StudentID, FirstName, MiddleName, LastName, Branch, Marks
        FROM inserted;

    OPEN cur;

    FETCH NEXT FROM cur INTO @StudentID, @FullName, @Branch, @Marks;

    WHILE @@FETCH_STATUS = 0
    BEGIN
        -- Combine Full Name
        SET @FullName = CONCAT(@FirstName, ' ', @MiddleName, ' ', @LastName);

        -- Retrieve Location
        SELECT @Location = StudentAddress
        FROM Address
        WHERE StudentID = @StudentID;

        -- If Marks >= 40, execute the procedure
        IF @Marks >= 40
        BEGIN
            EXEC AddToStudentStats
                @StudentID = @StudentID,
                @FullName = @FullName,
                @Branch = @Branch,
                @Percentage = @Marks,
                @Location = @Location;
        END;

        FETCH NEXT FROM cur INTO @StudentID, @FullName, @Branch, @Marks;
    END;

    CLOSE cur;
    DEALLOCATE cur;
END;
