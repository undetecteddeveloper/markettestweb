Steps & subject:
C&D (agent & engineer) ---> Coding (agent) ---> Updating (agent) ---> Testing (engineer) ---> Git (agent)
Trigger Events:
#Trigger Workflow
TE1: Prompt có "Thực hiện feature sau" ---> start Workflow.
#TE for C&D
TE2: Prompt có "Đã thống nhất. Bắt đầu code" ---> agent goes to Coding step.
TE3: "Chưa được, tôi explain lại: <liệt kê>" ---> start over C&D.
#TE for Coding 
TE4: Code xong ---> agent notifies trong respone và go to Updating step automatically.
#TE for Updating
TE5: Update xong ---> agent notifies trong respone và chờ TE6.
#TE for Testing
TE6: Prompt có "Ổn, đi tiếp" ---> agent goe to Git step automatically.
TE7: Prompt có "Chưa ổn, quay lại C&D" ---> agent roll back to C&D step, tiếp tục đến Testing, giữ all previous context và overwrite existing Updating txt file (no new file).
TE8: Prompt có "Chạy npm test", agent thực hiện prompt, rồi chờ TE6.
#TE for Git 
TE9:  git add all changes, commit + message rồi push lên repo ---> notifies trong respone và đợi TE1.

