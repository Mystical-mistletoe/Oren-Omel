namespace consoleProject
{
    /*
        * ФИО студента: Омельницкая ЕИ
        * номер варианта: 3
        * условие задачи (скопировать из листа задания):
        * 
        * Дан массив вещественных чисел, заполненный через 
        * список инициализаторов. (минимальное количество 
        * элементов – 10). 
        * Перезапишите значения этих 
        * элементов в массив целых чисел, отбрасывая 
        * дробную часть, выведите содержимое массива. 
        * 
        * Сделайте переворот целочисленного массива 
        * поэлементно без использования метода Reverse() 
        * и при выводе выделите цветом максимально приближенное к среднее значение массива.
        */
    internal class Program
    {
        static void Main(string[] args)
        {
            // Создаем массив для 15 случайных чисел
            int n = 15;
            double[] numbers = new double[15];
            Random random = new Random();
            double center = 0;


            // Заполнение массива случайными значениями от 0 до 10
            for (int i = 0; i < numbers.Length; i++)
            {
                numbers[i] = Math.Round(random.NextDouble() * (10.0 - 0.0) + 0.0, 2);
            }


            //отброс дробной части
            for (int i = 0; i < numbers.Length; i++)
            {
                int x = (int)numbers[i];
                numbers[i] = x;
            }

            //реверс массива
            for (int i = 0; i < numbers.Length / 2; i++)
            {
                int temp = (int)numbers[i];
                int temp2 = (int)numbers[n - 1 - i];
                numbers[i] = temp2;
                numbers[n - i - 1] = temp;
            }

            //вычисление среднего значения
            float summ = 0;
            foreach (int i in numbers)
                summ += i;
            center = summ / numbers.Length;

            //выделение цветом среднего значения массива
            for (int i = 0; i < numbers.Length; i++)
            {
                if (numbers[i] == center)
                {
                    Console.ForegroundColor = ConsoleColor.Green;
                    Console.Write(numbers[i] + " ");
                    Console.ForegroundColor = ConsoleColor.White;
                }
                else //в противном случае при выводе фон не меняется
                {
                    Console.Write(numbers[i] + " ");
                }
            }
        }
    }
}
