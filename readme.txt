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



