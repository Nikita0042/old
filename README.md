PART 1
1) Cоздаю пустой репозиторий lab02 (через сайт)
2) > $ nano README.md  (создаю файл и открываю его редактирование через встроенный в терминал текстовый редактор “nano”)

> $ git add README.md (добавляю созданный файл в репозиторий)

> $ git commit -m"Start" (добавляю комментарий)

> $ git push origin main (отсылаю изменения на глобальный репозиторий)


3) > $ nano hello_world.cpp (создаю файл с раширением .срр)

#include <iostream> 
   using namespace std;   
int main (){        
cout << "Hello world"<<endl;    
}
Добавляю этот файл в локальную копию репозитория: $ git add hello_world.cpp 
Закоммичиваю изменения с сообщением: $ git commit -m"added ‘hello_world’"
Изменяю исходный код так:

> $ nano hello_world.cpp
  
  #include <iostream>   
#include <string>   
using namespace std;   
int main (){    
 string name;   
cin.ignore();   
 getline(cin, name);    
 cout << "Hello world from " << name << "\n";   
}
Закоммичиваю новую версию программы. 

> $	git commit -m"change in hello_world" -a

Нет необходимости добавлять повторно hello_world с помощью git add, потому что мы его уже добавили, и этот файл теперь будет отслеживаться автоматически, однако коммитить нужно с опцией -а.

4) > $ git push origin main

Доказательство: скриншот 1

PART 2

1) > $ git branch patch1 (создаем новую ветку)
 
2) > $ git checkout patch1 (переключаемся на нее)
 
> $ nano hello_world.cpp
      #include <iostream>
    #include <string>

    int main (){
        std::string name;
        std::cin.ignore();
        std::getline(std::cin, name);
        std::cout << "Hello world from " << name << std::endl;
    }

> $ git commit -m"change in hello_world" -a
> $ git push origin patch1

Berendei-Jr wants to merge 1 commit into main from patch1
  >    $ nano hello_world.cpp
#include <iostream>
int main (){
    std::string str;
    std::cin >> str;
    std::cout << "Hello world from " << str << "\n";
}
// Hi guys!
     > $ git commit -m"added comment" -a
     > $ git push origin patch1
 
Скриншот 2

> $ git checkout main
> $ git pull origin main
Смотрим историю через команду: 
> $ git log

Скриншот 3

> $ git branch -D patch1
  
Deleted branch patch1 (was 1699890).

PART 3

> $ git branch patch2

> $ git checkout patch2

Необходимо 	установить утилиту clang-format командой $ sudo apt install clang-format

> $ clang-format -style=Mozilla hello_world.cpp

> $ git commit -m"style=Mozilla" -a
> 
> $ git 	push origin patch2

Berendei-Jr wants to merge 1 commit into main from patch2
// Hi pals!
This branch has conflicts that must be resolved

Скриншот 4

> $ git fetch origin
 
> $ git checkout -b patch2 origin/patch2

> $ git merge main

> $ git checkout main

> $ git merge --no-ff patch2

> $ git commit -m"comment" -a

> $ git pull origin main

> $ git push origin main
