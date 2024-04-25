# Introduction

Both VB.NET and C# can for the most part perform the same task although C# has matured pasted VB.NET but for standard task both are equal yet different syntax.

Below are two examples of the same code in VB.NET and C#.

```vb
Module Program
    '
    ' Class level variables
    '
    Private pSomeVar As Integer = 1
    Sub Main(args As String())


        ' declare variable
        Dim strFirstName = "Karen"
        Dim lastName As String = "Payne"

        ' declare and initialize variable
        Dim someList As New List(Of String) From {"one", "two", "three"}

        ' loop through list
        ' and display each element
        For Each item As String In someList
            Console.WriteLine(item)
        Next

        ChangeValue()
        Console.WriteLine(pSomeVar)
        Console.ReadLine()

    End Sub

    Sub ChangeValue()
        pSomeVar = 2
    End Sub
End Module

Public Class SqlStatements

    Public Shared ReadOnly Property InsertPeople As String
        Get
            Return _
                <SQL>
                    INSERT INTO dbo.Person
                    (
                        FirstName,
                        LastName,
                        BirthDate
                    )
                    VALUES
                    (@FirstName, @LastName, @BirthDate);
                    SELECT CAST(scope_identity() AS int);
                    </SQL>.Value

        End Get
    End Property

End Class
```

```csharp
internal class Program
{
    /*
     *  Class level variables
     */
    private static int pSomeVar = 1;

    static void Main(string[] args)
    {
        // declare variable
        var strFirstName = "Karen";
        string strLastName = "Payne";

        List<string> someList = ["Karen", "Payne"];

        // loop through list
        // and print out each item
        foreach (var item in someList)
        {
            Console.WriteLine(item);
        }

        ChangeValue();
        Console.WriteLine(pSomeVar);

        Console.ReadLine(); 
    }

    private static void ChangeValue()
    {
        pSomeVar = 2;
    }
}

public class SqlStatements
{
    public static string InsertPeople => 
        """
        INSERT INTO dbo.Person
        (
            FirstName,
            LastName,
            BirthDate
        )
        VALUES
        (@FirstName, @LastName, @BirthDate);
        SELECT CAST(scope_identity() AS int);
        """;
}
```