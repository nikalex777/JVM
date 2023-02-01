public class JvmComprehension {

//Класс JvmComprehension загружается ClassLoader'ом
и перемещается в Metaspace, где хранятся мета данные загруженных классов.

    public static void main(String[] args) {
// В стеке создается фрейм main.

        int i = 1;
// 1 - Создается переменная i типа int ей присваивается значением 1, "int i = 1" помещается во фрейм main.

        Object o = new Object();
// 2 - new Object() в куче выделяется память под новый объект, в стеке во фрейме main создается ссылка "о"
типа Object на выделенную область памяти в куче.

        Integer ii = 2;
// 3 - В куче выделяется память под новый объект Integer, в неё записывается значение "2", в стеке
во фрейме main создается ссылка "ii" на выделенную область памяти в куче.

        printAll(o, i, ii);
// 4 - В момент вызова метода "printAll" создаётся фрейм "printAll" в стеке. Во фрейме "printAll" создаются
ссылки на Object o, Integer ii, и храниться значение i типа int.

        System.out.println("finished"); 
// 7 - В стеке создается новый фрейм "println". Во фрейме "println" создается ссылки типа String на
объект в куче со значением "finished". Программа завершена фреймы удаляются.

    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   

// 5 - В куче выделяется память под новый объект Integer, в неё записывается значение "700",
в стеке во фрейме "printAll" создается ссылка "uselessVar" на выделенную область памяти в куче.
В коде отсутствуют ссылки на объект "uselessVar" он будет удален сборщиком мусора.

        System.out.println(o.toString() + i + ii);  

// 6 - В стеке создается фрейм "println". Во фрейме "println" передаются ссылки на Object o,
Integer ii, и храниться значение i типа int. Создастся новый фрейм "toString()". Во фрейме
"println" создается ссылка на строку "o.toString() + i + ii"

    }
}
