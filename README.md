
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <unistd.h>
#include <errno.h>
#include <sys/wait.h>

Int main()
{
  Int i ;
  Int from_child[2] ;
  Int to_child[2] ;
  Int tochild,fromchild ;

  /* ----------- Création du processus fils -------------*/
  If ( (i=fork() ) ) {
    If (i<0) {
      Perror(« Erreur de création du processus fils
      Exit(errno) ;
    }
    /* ----------- Parent --------------------*/
    Printf(«Le père connais le fils id = %d\ »,i) ;

    Printf(« Le père attend la fin du fils.\ ») ;
    Waitpid( i , NULL , 0 ) ;
  }
  /* ------------- Fils ---------------------*/
  Else {  //Dans le processus fils
    Printf(«Fils attend 2 seconds.\ ») ;
    Sleep(2) ;
    Printf(« Attente est terminée.\ ») ;
  }

  Printf(« …Fin.\ ») ;

  Return 0 ;
}
