һ�������汾�⡣
1. git init
�ѵ�ǰĿ¼���git���Թ���Ĳֿ�

2. git add XXX.txt
��XXX.txt��ӵ��ݴ�������ȥ
3. git commit -m "msg"
����git�����ļ��ύ���ֿ�

4. git status
�鿴�Ƿ����ļ�δ�ύ
5. git diff XXX.txt
�鿴XXX.txt�ļ��Ķ���ʲô���ݵ�δ���ύ

�����汾����
1. git log / git log --pretty=oneline
�鿴��ʷ��¼

2. ���˵���N���汾
git reset --hard HEAD^��N���汾��N��^
git reset --hard HEAD~1��N���汾�Ͱ�"1"����"N"

3. ���˵�ָ���汾�ŵİ汾
git reset --hard �汾��
4. git reflog
��ȡÿ���ύ�İ汾��

���������޸ĺ�ɾ���ļ�����
1. git checkout -- XXX.txt
���һ��add���ݴ��� - commit - �޸��� - "�����޸�" - �������������޸ģ��ص��Ͱ汾��һ����״̬���޸�֮ǰ��״̬��
�������add���ݴ��� - �޸��� - "�����޸�" - �ص�����ݴ������״̬���޸�֮ǰ��״̬��

2. rm XXX.txt + git commit -m "msg"
ɾ���ļ����Ӱ汾����ɾ����

�ġ�Զ�ֿ̲�GitHub
1. ����SSH Key
1.1. ���û���Ŀ¼�£�������û��.sshĿ¼������У��ٿ������Ŀ¼����û��id_rsa��id_rsa.pub�������ļ�������еĻ���ֱ������������������û�еĻ����������У������������
ssh-keygen  -t rsa �CC ��youremail@example.com��
1.2. id_rsa��˽Կ������й¶��ȥ��id_rsa.pub�ǹ�Կ�����Է��ĵظ����κ��ˡ�

2. ��¼github,�򿪡�settings���е�SSH Keysҳ�棬Ȼ������Add SSH Key��,��������title����Key�ı��������id_rsa.pub�ļ������ݡ�

3. ������Զ�̿⣿
��¼github�ϣ�Ȼ�������Ͻ��ҵ���create a new repo������һ���µĲֿ⡣

4. ������ʾ�����󣬽�����Ҫ�Ĳ���



��

�������������Ѿ��ڱ��ش�����һ��Git�ֿ��������github����һ��Git�ֿ⣬����ϣ���������ֿ����Զ��ͬ��������github�Ĳֿ������Ϊ���ݣ��ֿ���������ͨ���òֿ���Э����
�������£�1. �����µĲֿ� 2. �ڱ��ص�testgit�ֿ����������git remote add origin https://github.com/XXX/YYY.git + git push -u origin master
ע�⣺
* ʹ�� git push ���ʵ�����ǰѵ�ǰ��֧master���͵�Զ�̣��ѱ��ؿ���������͵�Զ�̡�
* ����Զ�̿��ǿյģ���һ������master��֧ʱ�������� �Cu������Git������ѱ��ص�master��֧�������͵�Զ���µ�master��֧������ѱ��ص�master��֧��Զ�̵�master��֧�������������Ժ�����ͻ�����ȡʱ�Ϳ��Լ����
** ��������ֻҪ���������ύ���Ϳ���ͨ���������git push origin master�����ɰѱ���master��֧�������޸����͵�github���ˡ�

�塢��¡Զ�ֿ̲�
1. git clone https://github.com/leeJiahuan/testGit2.git

����������ϲ���֧
ע�⣺HEADָ��ľ��ǵ�ǰ��֧��master����ָ���ύ��
1. �鿴��֧��git branch
* ���г����еķ�֧����ǰ��֧ǰ������һ���Ǻ�
2. ������֧��git branch branchname
3. �л���֧��git checkout branchname
4. �������л���֧��git checkout -b branchname
�൱���������git branch branchname + git checkout branchname
5. �ϲ�ָ����֧����ǰ��֧�ϣ�git merge otherbranchname
* ͨ���ϲ���֧ʱ��gitһ��ʹ�á�Fast forward��ģʽ��������ģʽ�£�ɾ����֧�󣬻ᶪ����֧��Ϣ��
* ʹ�� git merge --no-ff  -m "ע��" otherbranchname����ʾ����fast forwardģʽ��
6. ɾ����֧��git branch -d branchname

�ߡ����ص�ǰ�����ֳ�
���賡����master ����֧��dev ��ǰ���ڽ��п����ķ�֧��δadd���ݴ�������bugline ��master���������޸�����bug����ʱ��֧

1. �ڵ�ǰ������֧�½���ǰ�Ĺ����ֳ�����������(dev)ʹ������git stash��
2. �л���master��֧��(dev)ʹ������git checkout master
3. �������л���һ����ʱ��֧��(master)ʹ������git checkout -b bugline
4. �޸�bug
5. add ���ݴ��� �� commit��(bugline)ʹ������git add XXX.txt + git commit -m "msg"
6. �޸���ɺ��л�������֧�ϣ�����ɺϲ���(bugline)git checkout master + (master)git merge --no-ff -m "msg" bugline
7. ɾ����ʱ��֧��(master)ʹ������git branch -d bugline
8. ���ع�����֧��(master)ʹ������git checkout dev
* ע�⣺��ʱ�鿴�������Ǹɾ��ģ�(dev)ʹ������git status
9. �鿴���б����ص��ļ��б�(dev)ʹ������git stash list
10.�ָ������ֳ���
10.1. ʹ������ git stash apply �ָ����ָ���stash���ݲ���ɾ��������Ҫʹ������git stash drop��ɾ����
10.2. ʹ������ git stash pop �ָ����ָ���ͬʱ��stash����Ҳɾ���ˡ�

�ˡ�����Э��
�鿴Զ�̿����Ϣ��ʹ�� git remote
�鿴Զ�̿����ϸ��Ϣ��ʹ�� git remote �Cv

����Э������ģʽһ���������ģ�
1. ���ȣ�������ͼ��git push origin branch-name�����Լ����޸ģ�
2. �������ʧ�ܣ�����ΪԶ�̷�֧����ı��ظ����磬��Ҫ����git pull��ͼ�ϲ���
3. ����ϲ��г�ͻ������Ҫ�����ͻ�����ڱ����ύ������git push origin branch-name���͡�

��һ�����ͷ�֧
* ���ͷ�֧���ǰѸ÷�֧�����б����ύ��Զ�̿��У�����ʱ��Ҫָ�����ط�֧��������Git�ͻ�Ѹ÷�֧���͵�Զ�̿��Ӧ��Զ�̷�֧�ϡ�
* ʹ������ git push origin branchname

* һ������£���Щ��֧Ҫ�����أ�
** master��֧������֧�����Ҫʱ����Զ��ͬ����
** һЩ�޸�bug��֧����Ҫ���͵�Զ��ȥ�������Ⱥϲ�������֧�ϣ�Ȼ�������֧master���͵�Զ��ȥ���ɡ�


��������ȡ��֧
* ��ȡ��֧���ǰ�Զ�̵�origin��dev��֧������������
* ʹ�����������dev��֧��git checkout  �Cb dev origin/dev


