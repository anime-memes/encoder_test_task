# encoder_test_task
Составление системы кодирования команд

Запуск - ruby encoder.rb "#{json со списком инструкций}"

test.json - входной файл из задания, test1.json - мой тест

Результат работы - out.json

Основная идея алгоритма в том, что чем чаще встречается операнд, тем раньше выделяем ему биты (подсчитываем количество использований для каждого операнда и сортируем по убыванию).
Создаём диапазон с началом в текущем бите и концом в длине, указанной в json'е, сдвигаем текущий бит на длину поля и повторяем для следующего операнда. Затем пересекаем все диапазоны для одного операнда, чтобы найти точное место.

Пример: есть операнд A с длиной поля 5 и тремя диапазонами - (2..24), (6..24), (3..24). Пересекаем и получаем диапазон (6..24). Это значит, что старший бит для поля - 24-6+1=19, младший - 19+5-1=23. Таким образом, для каждой инструкции и для каждого формата этот операнд будет находиться в одном и том же месте.