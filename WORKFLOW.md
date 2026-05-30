# Steps & subject:
C&D (agent & engineer) ---> Coding (agent) ---> Updating (agent) ---> Testing (engineer hoặc agent) ---> Git (agent)
Trigger Events:
# Trigger Workflow
TE1: Prompt yêu cầu làm một việc có liên quan đến project ---> start Workflow.
# TE for C&D
TE2: Prompt yêu cầu code ---> agent goes to Coding step.
TE3: Prompt yêu sửa lại understanding cho agent ---> start over C&D.
# TE for Coding 
TE4: Code xong ---> agent notifies trong respone và go to Updating step automatically.
#TE for Updating
TE5: Update xong ---> agent notifies trong respone và chờ TE6.
# TE for Testing
TE6: Prompt xác nhận code ổn ---> agent goes to Git step automatically.
TE7: Prompt yêu cầu sửa lại ---> agent rolls back to C&D step (ngoại trừ TE8), tiếp tục đến Testing, giữ all previous context và overwrite existing Updating txt file (no new file).
TE8: Prompt yêu cầu agent tự test, agent tự screentshot (đã quy định trong CLAUDE.md). Nếu current page khớp template < 90%, agent rolls back to Coding step; khớp template > 90%, tự động go to Git step.
# TE for Git 
TE9:  git add all changes (ngoại trừ tệp hoặc folder không liên quan đến việc website chạy), commit + message rồi push lên repo ---> notifies trong respone và đợi TE1.

repo link tại: repo_link.txt