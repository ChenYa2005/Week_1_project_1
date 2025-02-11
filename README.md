# Week_1_project_1
RM homework for week1
#include <iostream>
#include <string>
#include <sstream>
#include <array>
#include <cmath>

using namespace std;

int main() {
    int x = 0, y = 0;
    array<int, 4> dx = {0, 1, 0, -1}; 
    array<int, 4> dy = {1, 0, -1, 0}; 
    array<string, 4> dir_names = {"上", "右", "下", "左"};
    int dir = 0; // 0: 上, 1: 右, 2: 下, 3: 左

    cout << "请输入指令（按Ctrl+D或Ctrl+Z结束）：\n";

    string command;
    while (getline(cin, command)) {
        istringstream iss(command);
        string action;
        iss >> action;

        if (action == "w" || action == "s") {
            int steps;
            iss >> steps;
            int dx_step = dx[dir];
            int dy_step = dy[dir];
            if (action == "s") {
                dx_step *= -1;
                dy_step *= -1;
            }
            x += dx_step * steps;
            y += dy_step * steps;
        } else if (action == "d") { 
            dir = (dir + 1) % 4;
        } else if (action == "a") { 
            dir = (dir - 1 + 4) % 4;
        }

        cout << "位置: (" << x << ", " << y << "), 方向: " << dir_names[dir] << ".\n";
    }

    return 0;
}
