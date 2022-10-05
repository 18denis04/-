#include <iostream>
#include <fstream>
#include <string>

void line(const char *FIL){
    std::ifstream file(FIL);
    int counter=0;
    char* lin = new char [1000];
    while (!file.eof()){
        file.getline(lin, 1000, '\n');
        counter += 1;
    }
    std::cout << counter << ' ';
    file.close();
}
void bit(const char *FIL){
    FILE * file_in = fopen(FIL, "r");
    fseek(file_in, 0, SEEK_END);
    auto result = ftell(file_in);
    std::cout << result << ' ';
    }
void words(const char *FIL) {
    std::freopen(FIL, "r", stdin);
    int count = 0;
    for (char word[100500]; std::cin >> word; ++count);
    std::cout << count << " ";
}
int main(int argc, char** argv) {
    int w = 0, l =0, c = 0;
    const char *FIL = "пусто";
    for(int i = 1; i<argc; i++){
        if(argv[i][0]!= '-') FIL = argv[i];
    }
    if (FIL =="пусто"){std::cout<<"no name of file";return 0;}
    if (argc==1){std::cout<<"only name of the programm";}
    if (argc==2){words(FIL);bit(FIL);line(FIL);std::cout<<FIL;}
    for(int i = 1; i<argc; i++){
        std::string tsk=argv[i];
        if(argv[i][0] == '-' & argv[i][1] != '-'){
            for (int j=1;j<tsk.length();j++){
                if(tsk[j] == 'l'& l != 1){ line(FIL); l++;}
                if(tsk[j] == 'w'& w != 1){ words(FIL); w++;}
                if(tsk[j] == 'c'& c != 1){ bit(FIL); c++;}
            }
        }
        if(argv[i][0] == '-' & argv[i][1] == '-'){
            if(tsk == "--words" & w != 1){ words(FIL); w++;}
            if(tsk == "--bytes" & c != 1){ bit(FIL); c++;}
            if(tsk == "--lines" & l != 1){ line(FIL); l++;}
        }
    }
    std::cout << FIL;
    std::cout << FIL;
    return 0;
}
