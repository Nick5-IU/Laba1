Домашняя работа
Студента группы ИУ8-21 Морозова Николая

Скачайте библиотеку Boost с помощью утилиты wget:

$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
вывод в файле wget-log

Разархивируйте скачанный файл в директорию ~/boost_1_69_0:

$ tar -xzvf boost_1_69_0.tar.gz -C ~/
вывод в файле tar_output

Подсчитайте количество файлов в директории ~/boost_1_69_0 (не включая вложенные директории):

$ find ~/boost_1_69_0 -maxdepth 1 -type f | wc -l
12
Подсчитайте количество файлов в директории ~/boost_1_69_0 (включая вложенные директории):

$ find ~/boost_1_69_0 -type f | wc -l
61191
Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, и остальных файлов:

$ find ~/boost_1_69_0 -type f -name "*.hpp" | wc -l
$ find ~/boost_1_69_0 -type f -name "*.cpp" | wc -l
$ find ~/boost_1_69_0 -type f ! -name "*.hpp" ! -name "*.cpp" | wc -l
14912
13774
32505
Найдите полный путь до файла any.hpp внутри библиотеки Boost:

$ find ~/boost_1_69_0 -name "any.hpp"
/home/mordecai/boost_1_69_0/boost/type_erasure/any.hpp
/home/mordecai/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
/home/mordecai/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
/home/mordecai/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
/home/mordecai/boost_1_69_0/boost/fusion/include/any.hpp
/home/mordecai/boost_1_69_0/boost/hana/any.hpp
/home/mordecai/boost_1_69_0/boost/hana/fwd/any.hpp
/home/mordecai/boost_1_69_0/boost/proto/detail/any.hpp
/home/mordecai/boost_1_69_0/boost/any.hpp
/home/mordecai/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
Выведите в консоль все файлы, где упоминается последовательность boost::asio:

$ grep -rl "boost::asio" ~/boost_1_69_0
вывод в файле boost_asio_files

Скомпилируйте Boost. Вы можете следовать инструкции из официальной документации:

$ cd ~/boost_1_69_0
./bootstrap.sh
./b2
вывод в b2_output и bootstrap_output

Перенесите все скомпилированные статические библиотеки в директорию ~/boost-libs:

$ mkdir -p ~/boost-libs
find ~/boost_1_69_0 -name "*.a" -exec mv {} ~/boost-libs \;
Подсчитайте, сколько занимает дискового пространства каждый файл в этой директории

$ du -h ~/boost-libs/*

4,0K	/home/mordecai/boost-libs/libboost_atomic.a
232K	/home/mordecai/boost-libs/libboost_chrono.a
152K	/home/mordecai/boost-libs/libboost_container.a
20K	/home/mordecai/boost-libs/libboost_context.a
320K	/home/mordecai/boost-libs/libboost_contract.a
152K	/home/mordecai/boost-libs/libboost_date_time.a
4,0K	/home/mordecai/boost-libs/libboost_exception.a
232K	/home/mordecai/boost-libs/libboost_fiber.a
404K	/home/mordecai/boost-libs/libboost_filesystem.a
828K	/home/mordecai/boost-libs/libboost_graph.a
276K	/home/mordecai/boost-libs/libboost_iostreams.a
208K	/home/mordecai/boost-libs/libboost_prg_exec_monitor.a
1,5M	/home/mordecai/boost-libs/libboost_program_options.a
80K	/home/mordecai/boost-libs/libboost_random.a
3,1M	/home/mordecai/boost-libs/libboost_regex.a
1,2M	/home/mordecai/boost-libs/libboost_serialization.a
36K	/home/mordecai/boost-libs/libboost_stacktrace_addr2line.a
20K	/home/mordecai/boost-libs/libboost_stacktrace_backtrace.a
16K	/home/mordecai/boost-libs/libboost_stacktrace_basic.a
4,0K	/home/mordecai/boost-libs/libboost_stacktrace_noop.a
4,0K	/home/mordecai/boost-libs/libboost_system.a
2,2M	/home/mordecai/boost-libs/libboost_test_exec_monitor.a
52K	/home/mordecai/boost-libs/libboost_timer.a
2 ,2M	/home/mordecai/boost-libs/libboost_unit_test_framework.a
4,5M	/home/mordecai/boost-libs/libboost_wave.a
776K	/home/mordecai/boost-libs/libboost_wserialization.a
Найдите топ 10 самых "тяжёлых" файлов
$ du -ah ~/boost-libs | sort -rh | head -n 10

19M	/home/mordecai/boost-libs
4,5M	/home/mordecai/boost-libs/libboost_wave.a
3,1M	/home/mordecai/boost-libs/libboost_regex.a
2,2M	/home/mordecai/boost-libs/libboost_unit_test_framework.a
2,2M	/home/mordecai/boost-libs/libboost_test_exec_monitor.a
1,5M	/home/mordecai/boost-libs/libboost_program_options.a
1,2M	/home/mordecai/boost-libs/libboost_serialization.a
828K	/home/mordecai/boost-libs/libboost_graph.a
776K	/home/mordecai/boost-libs/libboost_wserialization.a
404K	/home/mordecai/boost-libs/libboost_filesystem.a
