# example-revert

### เลข has อาจไม่เหมือนกัน เนื่องจากความแตกต่างของเครื่อง


1. ทำการ ใช้ git Clone `https://github.com/nethuhu33799/ex-revert.git` repository ใน cmd หน้า desktop
    ```bash
    $ git clone https://github.com/nethuhu33799/ex-revert.git
    ```
    เข้าไปหา โฟรเดอร์ที่เรา clone มา
    ```bash
    $ cd ex-revert
    ```
2. ใช้ ``` git log --all --oneline --graph```
    ```bash
    $ git log --oneline --graph --all
    * 5734e08 (HEAD -> main, origin/main) commit-4  <--มันผิดพลาด อยาก undo
    * 571a269 commit-3
    | * 4018d90 (from_commit-2) commit2.1
    |/  
    * a0666ba commit-2
    * 6e80f82 commit-1
    * 21eb0b1 Initial commit
    ```


3. ทำการตั้งค่า Configure 
    ```bash
    $ git config --global user.name "<ชื่อน้องไงก็ได้>" 
    $ git config --global user.email "<xxx+nethuhu33799@users.noreply.github.com.>"
    ```
4. การใช้คำสั่ง `revert` เพื่อทำการ ยกเลิก `commit ล่าสุด`
    * ก่อนทำ
    ```bash
    $ git log --oneline --graph --all
    * 5734e08 (HEAD -> main, origin/main) commit-4
    * 571a269 commit-3
    | * 4018d90 (from_commit-2) commit2.1
    |/  
    * a0666ba commit-2
    * 6e80f82 commit-1
    * 21eb0b1 Initial commit
    ```
    ให้น้องใช้คำสั่ง
    `git revert <has ของ commit-4>` เลขของพี่จะเป็น 5734e08
    ```bash
    git revert 5734e08
    ```
    ถ้ามีหน้าต่างเด้ง ให้กด commit ตามที่มันให้

    * หลังทำ

    ```bash
        $ git log --oneline --graph --all
        * 962fc30 (HEAD -> main) Revert "commit-4"
        * 5734e08 (origin/main, origin/HEAD) commit-4
        * 571a269 commit-3
        | * 4018d90 (from_commit-2) commit2.1
        |/  
        * a0666ba commit-2
        * 6e80f82 commit-1
        * 21eb0b1 Initial commit    
    ```

4. ทำการ `push` remote repository.
    ```bash
    $ git push -u origin main
    ```
ถ้าทำการ push ครั้งแรก จะใช้แบบ `$ git push -u origin main` เพื่อทำหมด เส้นทางครั้งแรกที่จะส่งไป ครั้งต่อไปทำแค่ `git push`

*** สิ่งที่พี่ต้องการให้เห็นคือ เมื่อน้องทำการ `revert commit 4` พี่อยากให้น้อง สั่งเกตุว่า `commit Revert "commit-4"` กับ `commit-4` ต่างกันอย่างไร ***
**น้องสามารถ`git checkout` ไปมาเมื่อดูความเปลี่ยนแปล่งที่พี่บอกว่า มันเหมือน `undo` เอาอันเก่ามาทับอันที่ผิด โดย commit ทุกอันก็อยู่ครบ**