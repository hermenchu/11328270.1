# 11328270.1
## 1.0
### 1.1
#### 1.2
def add_task():
    print("Add task")

def show_tasks():
    print("Show tasks")

def main():
    while True:
        print("\n=== To-Do List 管理系統 ===")
        print("1. 顯示任務清單")
        print("2. 新增任務")
        print("3. 離開系統")
        
        choice = input("請選擇功能（輸入數字）：").strip()
        
        if choice == "1":
            show_tasks()
        elif choice == "2":
            add_task()
        elif choice == "3":
            print("感謝使用，再見！")
            break
        else:
            print("無效的選擇，請重新輸入。\n")

# 啟動主程式
main()

# 全域變數：用來存儲任務
pending_tasks = []   # 待完成的任務清單
completed_tasks = [] # 已完成的任務清單
# 新增任務
def add_task():
    title = input("請輸入任務名稱：").strip()
    if not title:
        print("任務名稱不可為空！")
        return
    
    description = input("請輸入任務描述（可選）：").strip()
    due_date = input("請輸入完成期限（格式: YYYY-MM-DD，可選）：").strip()

    # 建立新任務
    new_task = {
        "title": title,
        "description": description or None, # 這邊用 None 的話，後面 task['description'][:40] 會產生錯誤！
        "due_date": due_date or None,
    }
    pending_tasks.append(new_task)
    print(f"\n成功新增任務：{new_task['title']}\n")
    import sys
from PyQt6.QtWidgets import QApplication, QLabel, QPushButton
from PyQt6.QtWidgets import QVBoxLayout, QWidget

class MainWindow(QWidget):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("PyQt6 基本 GUI")
        self.resize(400, 300)

        # 建立標籤與按鈕
        self.label = QLabel("按下按鈕開始計數！", self)
        self.button = QPushButton("點擊我", self)

        # 計數變數
        self.counter = 0

        # 設定佈局
        layout = QVBoxLayout()
        layout.addWidget(self.label)
        layout.addWidget(self.button)
        self.setLayout(layout)

        # 連接按鈕點擊事件
        self.button.clicked.connect(self.increment_counter)

    def increment_counter(self):
        self.counter += 1
        self.label.setText(f"按鈕已被點擊 {self.counter} 次！")

# 主程式入口
if __name__ == "__main__":
    app = QApplication(sys.argv)
    window = MainWindow()
    window.show()
    sys.exit(app.exec())