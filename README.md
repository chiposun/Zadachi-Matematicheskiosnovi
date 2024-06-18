1 zad 
///////////////////////////
using System;

class Program
{
    static string ConvertNumber(string number, int fromBase, int toBase)
    {
        int decimalNumber = Convert.ToInt32(number, fromBase);
        return Convert.ToString(decimalNumber, toBase).ToUpper();
    }

    static void Main()
    {
        Console.Write("Enter the number: ");
        string number = Console.ReadLine();
        Console.Write("Enter the source base: ");
        int fromBase = int.Parse(Console.ReadLine());
        Console.Write("Enter the target base: ");
        int toBase = int.Parse(Console.ReadLine());

        string convertedNumber = ConvertNumber(number, fromBase, toBase);
        Console.WriteLine($"Converted number: {convertedNumber}");
    }
}

///////////////////////////////
zad 2 
/////////////////////////////
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    static void Main()
    {
        Console.Write("Enter the list of numbers separated by space: ");
        List<int> numbers = Console.ReadLine().Split().Select(int.Parse).ToList();

        double average = numbers.Average();
        double median = numbers.OrderBy(n => n).Median();
        int mode = numbers.GroupBy(n => n).OrderByDescending(g => g.Count()).First().Key;

        Console.WriteLine($"Средно Аритметично: {average}");
        Console.WriteLine($"Медиана: {median}");
        Console.WriteLine($"Мода: {mode}");
    }
}

public static class IEnumerableExtensions
{
    public static double Median(this IEnumerable<int> source)
    {
        var sortedList = source.OrderBy(n => n).ToList();
        int count = sortedList.Count;
        if (count % 2 == 0)
        {
            return (sortedList[count / 2 - 1] + sortedList[count / 2]) / 2.0;
        }
        else
        {
            return sortedList[count / 2];
        }
    }
}
//////////////////////////////////
zad 3
\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\

using System;

class Program
{
    static void Main()
    {
        double[,] matrix = new double[3, 3];

        for (int i = 0; i < 3; i++)
        {
            Console.Write($"Enter row {i + 1} of the matrix: ");
            double[] row = Array.ConvertAll(Console.ReadLine().Split(), double.Parse);
            for (int j = 0; j < 3; j++)
            {
                matrix[i, j] = row[j];
            }
        }

        double determinant = CalculateDeterminant(matrix);
        Console.WriteLine($"Детерминанта: {determinant}");
    }

    static double CalculateDeterminant(double[,] matrix)
    {
        return matrix[0, 0] * (matrix[1, 1] * matrix[2, 2] - matrix[1, 2] * matrix[2, 1])
             - matrix[0, 1] * (matrix[1, 0] * matrix[2, 2] - matrix[1, 2] * matrix[2, 0])
             + matrix[0, 2] * (matrix[1, 0] * matrix[2, 1] - matrix[1, 1] * matrix[2, 0]);
    }
}
/////////////////////////
zad 4 
////////////////////////////
using System;
using System.Linq;
using MathNet.Numerics;

class Program
{
    static void Main()
    {
        Console.Write("Enter the coefficients of the polynomial: ");
        double[] coefficients = Array.ConvertAll(Console.ReadLine().Split(), double.Parse);
        
        var roots = FindRoots.Polynomial(coefficients);
        Console.WriteLine("Корените на полинома: " + string.Join(", ", roots));
    }
}
////////////////////////////
zad 5 
////////////////////////
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    static void Main()
    {
        List<double[]> vectors = new List<double[]>();

        while (true)
        {
            Console.Write("Enter a vector (or type 'done' to finish): ");
            string input = Console.ReadLine();
            if (input.ToLower() == "done")
            {
                break;
            }

            double[] vector = Array.ConvertAll(input.Split(), double.Parse);
            vectors.Add(vector);
        }

        double shortestLength = vectors.Min(v => Math.Sqrt(v.Sum(c => c * c)));
        Console.WriteLine($"Дължина на най-късият вектор: {shortestLength}");
    }
}
//////////////////////////////////////
zad 7 
//////////////////////////////////////

using System;

class Program
{
    static void Main()
    {
        Console.Write("Enter the first number: ");
        int n = int.Parse(Console.ReadLine());
        Console.Write("Enter the second number: ");
        int k = int.Parse(Console.ReadLine());

        int permutations = Permutations(n, k);
        int combinations = Combinations(n, k);
        int variations = Variations(n, k);

        Console.WriteLine($"Пермутации: {permutations}");
        Console.WriteLine($"Комбинации: {combinations}");
        Console.WriteLine($"Вариации: {variations}");
    }

    static int Factorial(int number)
    {
        int result = 1;
        for (int i = 1; i <= number; i++)
        {
            result *= i;
        }
        return result;
    }

    static int Permutations(int n, int k)
    {
        return Factorial(n) / Factorial(n - k);
    }

    static int Combinations(int n, int k)
    {
        return Factorial(n) / (Factorial(k) * Factorial(n - k));
    }

    static int Variations(int n, int k)
    {
        return Factorial(n) / Factorial(n - k);
    }
}
////////////////////////////////////
