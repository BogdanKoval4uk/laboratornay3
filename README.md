# Лабораторная работа номер 3
## Задание 1

Вам поручили перейти на систему автоматизированной сборки CMake. Исходные файлы находятся в директории formatter_lib. В этой директории находятся файлы для статической библиотеки formatter. Создайте CMakeList.txt в директории formatter_lib, с помощью которого можно будет собирать статическую библиотеку formatter.

## Задание 2

У компании "Formatter Inc." есть перспективная библиотека, которая является расширением предыдущей библиотеки. Т.к. вы уже овладели навыком созданием CMakeList.txt для статической библиотеки formatter, ваш руководитель поручает заняться созданием CMakeList.txt для библиотеки formatter_ex, которая в свою очередь использует библиотеку formatter.

## Задание 3

Конечно же ваша компания предоставляет примеры использования своих библиотек. Чтобы продемонстрировать как работать с библиотекой formatter_ex, вам необходимо создать два CMakeList.txt для двух простых приложений:

    hello_world, которое использует библиотеку formatter_ex;
    solver, приложение которое испольует статические библиотеки formatter_ex и solver_lib.
# Выполение работы
## Задание номер 1
 1) ![image](https://github.com/BogdanKoval4uk/laboratornay3/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202023-05-12%2020-04-34.png)
 2) ![image](https://github.com/BogdanKoval4uk/laboratornay3/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202023-05-17%2015-58-52.png)
 3) ![image](https://github.com/BogdanKoval4uk/laboratornay3/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202023-05-15%2011-01-36.png)
 

    Проверим, что проект собирается. Для этого в директории formatter_lib введём команды:

    $ cmake -B build
    $ cmake --build build

    Последней строкой консоль должна выдать [100%] Built target formatter_lib

cmake_minimum_require задает минимальную версию Cmake

Затем задаем стандарт C++

project(formatter) создаем проект formatter, к которому можно подключать исполняемы файлы и библиотеки

add_library(formatter STATIC formatter.cpp) создаем статическую библиотеку из данных файлов.
## Задание номер 2
1) ![image](https://github.com/BogdanKoval4uk/laboratornay3/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202023-05-17%2016-24-14.png)
2) ![image](https://github.com/BogdanKoval4uk/laboratornay3/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202023-05-17%2016-23-18.png)

Прописывается основная информация для сборки через CMake. cmake_minimum_required(VERSION 3.4) # Минимальная версия CMake

set(CMAKE_CXX_STANDARD 17) # Стандарт C++

set(CMAKE_CXX_STANDARD_REQUIRED ON) # Обязательность установки указанного стандарта (если OFF (по умолчанию), то воспринимается как совет)

Название проекта project()

Библиотека add_library(

my_very_interesting_target_library # Название цели

STATIC # Тип библиотеки (SHARED или STATIC)

${CMAKE_CURRENT_SOURCE_DIR}/path_to_cpp_file

${CMAKE_CURRENT_SOURCE_DIR}/path_to_another_cpp_file )

Указание директорий с заголовочными файлами target_include_directories(

target_name # Цель, при сборке которой учитываются указанные пути к заголовочным файлам

PUBLIC # область видимости (PRIVATE, INTERFACE или PUBLIC)

${CMAKE_CURRENT_SOURCE_DIR}/include ) Указание библиотек для линковки

target_link_libraries(

target_name # Цель, к которой просходит линковка

library_name # Библиотеки, которые линкуются к цели

)

add_subdirectory подключаем в сборку проект formatter из заданной директории

