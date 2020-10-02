# lab-resolving-git-conflicts

1 Solicita crear una bifurcación del repositorio de ironhack, LAB

 

2. ya dentro del respositrio en mi github, clonarlo a mi local

 

MacBook-Air-de-User:~ user$ git clone https://github.com/patocuak08/lab-resolving-git-conflicts.git
Cloning into 'lab-resolving-git-conflicts'...
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 9 (delta 0), reused 2 (delta 0), pack-reused 0
Unpacking objects: 100% (9/9), done.
MacBook-Air-de-User:~ user$ ls


3. colocarnos en la carpeta de lab-resolving-git-conflicts

MacBook-Air-de-User:~ user$ cd lab-resolving-git-conflicts
MacBook-Air-de-User:lab-resolving-git-conflicts user$ ls


4. En la guia se pedía que se hiciera un git pull origin master para fusionar automáticamente los códigos de mi repositorio local (compu) a la remota (github)



MacBook-Air-de-User:lab-resolving-git-conflicts user$ git pull origin master
From https://github.com/patocuak08/lab-resolving-git-conflicts
 * branch            master     -> FETCH_HEAD
Already up to date.



5. Debi de modificar el archivo your-code/about-me.md, agregando o quitando lo que yo quisiera. Posteriormente debo de hacer git add, git commit y git push. Para poder modificar me tuve que ir a jupyter notebook


MacBook-Air-de-User:lab-resolving-git-conflicts user$ jupyter notebook
[I 20:10:35.594 NotebookApp] JupyterLab extension loaded from /usr/local/Cellar/jupyterlab/2.2.4/libexec/lib/python3.8/site-packages/jupyterlab
[I 20:10:35.594 NotebookApp] JupyterLab application directory is /usr/local/Cellar/jupyterlab/2.2.4/libexec/share/jupyter/lab
[I 20:10:35.599 NotebookApp] Serving notebooks from local directory: /Users/user/lab-resolving-git-conflicts
[I 20:10:35.599 NotebookApp] Jupyter Notebook 6.1.1 is running at:
[I 20:10:35.599 NotebookApp] http://localhost:8888/?token=10ec8622ccae1b48f1f4e029adf04855aa1b4e13e11cfba6



DENTRO DE JUPYTER ENTRE AL ARCHIVO, MODIFIQUÉ Y GUARDÉ

 

MacBook-Air-de-User:lab-resolving-git-conflicts user$ git add .
MacBook-Air-de-User:lab-resolving-git-conflicts user$ git status

On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   .ipynb_checkpoints/mi_conflicto-checkpoint.ipynb
	modified:   lab-resolving-git-conflicts/your-code/about-me.md
	new file:   mi_conflicto.ipynb

MacBook-Air-de-User:lab-resolving-git-conflicts user$ git commit -m "Cambie el texto original de about-me"
[master 626c569] Cambie el texto original de about-me
 3 files changed, 71 insertions(+), 3 deletions(-)
 create mode 100644 .ipynb_checkpoints/mi_conflicto-checkpoint.ipynb
 create mode 100644 mi_conflicto.ipynb
MacBook-Air-de-User:lab-resolving-git-conflicts user$ git push
Counting objects: 7, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (7/7), 955 bytes | 955.00 KiB/s, done.
Total 7 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/patocuak08/lab-resolving-git-conflicts.git
   80f9a87..626c569  master -> master


6. PIDE AVERIGUAR EL ID DEL COMMIT EJECUCANTO git log


MacBook-Air-de-User:lab-resolving-git-conflicts user$ git log
commit 626c5694906f97abedfaa5a5d02df8c7df5e8a5b (HEAD -> master, origin/master, origin/HEAD)
Author: Pato Ceron <patricia.vceron@gmail.com>
Date:   Thu Oct 1 20:13:36 2020 -0500

    Cambie el texto original de about-me

commit 80f9a87e9c4e9bc7e3c0daa4ca94aa451ff7a442
Author: ta-data-mexpt <55260094+ta-data-mexpt@users.noreply.github.com>
Date:   Wed Mar 18 18:50:27 2020 -0600

    INIT



El primer Código del commit es el que pertenece a este ya que incluso ahí viene marcada la fecha y hora del cambio, ya que el que dicen “miércoles” fue un ejercicio durante la clase al cual no di commit. Descubra la confirmación inmediatamente antes de su confirmación reciente y copie su cadena de identificación.

7. Pide que regresemos a la confirmación antes de realizar el último cambio, el cual se hace así

MacBook-Air-de-User:lab-resolving-git-conflicts user$ git reset --hard 80f9a87e9c4e9bc7e3c0daa4ca94aa451ff7a442
HEAD is now at 80f9a87 INIT


8. Ahora mencioan que estoy en mi rama maestra, pero mi rama local esta todavía en el commit anterior al último que hice (onde modifiqué el archivo your-code/about-me.md

Debemos de agregar una rama llamada git checkout -b lab-resolving-git-conflict

MacBook-Air-de-User:lab-resolving-git-conflicts user$ git checkout -b lab-resolving-git-conflict
Switched to a new branch 'lab-resolving-git-conflict'


9. ya colocados en la nueva rama, debemos de abrir de nuevo el archivo your-code/about-me-md, eliminando todo el archivo y remplazándolo con una introducción sobre mi


MacBook-Air-de-User:lab-resolving-git-conflicts user$ git branch
* lab-resolving-git-conflict
  master
MacBook-Air-de-User:lab-resolving-git-conflicts user$ jupyter notebook



10. Dentro de jupyter edité mi presentación, es añadirla, confirmarla y obtener el ID del nuevo commit. 

 





MacBook-Air-de-User:lab-resolving-git-conflicts user$ git status
On branch lab-resolving-git-conflict
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   lab-resolving-git-conflicts/your-code/about-me.md

no changes added to commit (use "git add" and/or "git commit -a")


MacBook-Air-de-User:lab-resolving-git-conflicts user$ git add .
MacBook-Air-de-User:lab-resolving-git-conflicts user$ git commit -m "en la ueva rama, elimite el archivo about me y lo reemplace por informacion mia"
[lab-resolving-git-conflict 0258fa5] en la ueva rama, elimite el archivo about me y lo reemplace por informacion mia
 1 file changed, 16 insertions(+), 7 deletions(-)
 rewrite lab-resolving-git-conflicts/your-code/about-me.md (99%)

MacBook-Air-de-User:lab-resolving-git-conflicts user$ git log
commit 0258fa5e3b02ecd09ce0c65659accdf7fae3cff7 (HEAD -> lab-resolving-git-conflict)
Author: Pato Ceron <patricia.vceron@gmail.com>
Date:   Thu Oct 1 21:17:07 2020 -0500

    en la ueva rama, elimite el archivo about me y lo reemplace por informacion mia

commit 80f9a87e9c4e9bc7e3c0daa4ca94aa451ff7a442 (master)
Author: ta-data-mexpt <55260094+ta-data-mexpt@users.noreply.github.com>
Date:   Wed Mar 18 18:50:27 2020 -0600

    INIT



11. Posterior pide que ejecutemos un git pull origin master donde Git nos dirá que hay un conflicto que me impide fusionar las ramas.

MacBook-Air-de-User:lab-resolving-git-conflicts user$ git pull origin master
From https://github.com/patocuak08/lab-resolving-git-conflicts
 * branch            master     -> FETCH_HEAD
Auto-merging lab-resolving-git-conflicts/your-code/about-me.md
CONFLICT (content): Merge conflict in lab-resolving-git-conflicts/your-code/about-me.md
Automatic merge failed; fix conflicts and then commit the result.









MacBook-Air-de-User:lab-resolving-git-conflicts user$ git status
On branch lab-resolving-git-conflict
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:

	new file:   .ipynb_checkpoints/mi_conflicto-checkpoint.ipynb
	new file:   mi_conflicto.ipynb

Unmerged paths:
  (use "git add <file>..." to mark resolution)

	both modified:   lab-resolving-git-conflicts/your-code/about-me.md


PARA RESOLVER ESTO ABRIMOS Visual studio Y BUSCAMOS EL ARCHIVO ABOUT-ME, A ESTE LE PUSIMOS LA OPCIÓN DE MEZCLAR AMBOS ARCHIVOS, EL ORIGINAL (QUE APARECIA SIENDO EL MIO) Y EL ANTERIOR( DONDE PONIA LA LINEA QUITÉ LOS DOS ULTIMOS PARRAFOS) QUEDANDO ASÍ EN UN SOLO TEXTO
. Lo guardamos y pasamos a la terminal

 



MacBook-Air-de-User:lab-resolving-git-conflicts user$ git status
On branch lab-resolving-git-conflict
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:

	new file:   .ipynb_checkpoints/mi_conflicto-checkpoint.ipynb
	new file:   mi_conflicto.ipynb

Unmerged paths:
  (use "git add <file>..." to mark resolution)

	both modified:   lab-resolving-git-conflicts/your-code/about-me.md


AGREGAMOS Y CONFIRMAMOS CON UN MENSAJE


MacBook-Air-de-User:lab-resolving-git-conflicts user$ git add .
MacBook-Air-de-User:lab-resolving-git-conflicts user$ git commit -m "pude resolver el conflicto a traves de visual studio donde combiné ambos textos"
[lab-resolving-git-conflict 0f509db] pude resolver el conflicto a traves de visual studio donde combiné ambos textos
MacBook-Air-de-User:lab-resolving-git-conflicts user$ git status
On branch lab-resolving-git-conflict
nothing to commit, working tree clean
MacBook-Air-de-User:lab-resolving-git-conflicts user$ git push
fatal: The current branch lab-resolving-git-conflict has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin lab-resolving-git-conflict


AQUÍ EL MISMO GIT ME SUGIERE QUE USE EL GIT PUSH –SET -UPSTREAM 


MacBook-Air-de-User:lab-resolving-git-conflicts user$ git push --set-upstream origin lab-resolving-git-conflict
Counting objects: 10, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (8/8), done.
Writing objects: 100% (10/10), 2.12 KiB | 1.06 MiB/s, done.
Total 10 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), completed with 1 local object.
remote: 
remote: Create a pull request for 'lab-resolving-git-conflict' on GitHub by visiting:
remote:      https://github.com/patocuak08/lab-resolving-git-conflicts/pull/new/lab-resolving-git-conflict
remote: 
To https://github.com/patocuak08/lab-resolving-git-conflicts.git
 * [new branch]      lab-resolving-git-conflict -> lab-resolving-git-conflict
Branch 'lab-resolving-git-conflict' set up to track remote branch 'lab-resolving-git-conflict' from 'origin'.


POSTERIOR SOLO HICE EL PULL ENTRE EL REPOSITORIO DE IRONHACK Y EL MIO DONDE

BASE REPOSITORIO: ta-data-mexpt/lab-resolving-git-conflicts
BASE: MASTER
HEAD REPOSITORY: patocuak08/laboratorio-resolviendo-conflictos-git
COMPARE: laboratorio-resolviendo-conflictos-git

aL HACER ESTO SE GUARDARON TODOS LOS COMMITS PASO POR PASO DE LO QUE FUI HACIENDO PARA RESOLVER EL CONFLICTO, INCLUSO MISMO GIT AL OMENTO DE DARLE AL BOTON DE “PULL REQUEST” APARECÍA UN BOTÓN EN VERDE QUE DECIA “CREA PULL REQUUEST 5 CAMBIOS” Y AL DARLE ME ACOMODO POR DEFAULT LAS OPCIONES, YO SOLO LO REVISÉ Y DI ACEPTAR
