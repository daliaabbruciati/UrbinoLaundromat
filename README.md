# Urbino Laundromat
<h4>Progetto in Haskell per il corso di "Linguaggi di programmazione e verifica software"</h4>

<ul>
  <li>
    <strong><h4>Project specification</h4></strong>
    Urbino laundromat is now equipped with N concurrent automated stations working as follows. As a customer enters, she chooses a station and puts a coin into       the related slot to gain a token enabling a given available washing machine. In order to properly allocate the washing machines, the stations share a boolean     array available[NMACHINES], where NMACHINES is a constant indicating how many machines there are in the laundromat, and a semaphore nfree that in- dicates       how many machines are available. The pseudo-code executed by each station to allocate a machine and, therefore, issuing a token, is: <br>
    
    int allocate() 
    {
      P(nfree); /* Wait until a machine is available */
      for (int i=0; i < NMACHINES; i++)
          if (available[i] == TRUE) {
              available[i] = FALSE;
              return i;
      }
    } 
    
  [Reminder: the semaphore is equipped with two proper atomic operations, historically denoted as P and V: the former decrements the semaphore, while the latter   increments it. The domain of possible values for the semaphore is [0..NMACHINES].]
  After having obtained the token, the customer puts laundry into the al- located machine and inserts the token into the machine. When the machine finishes its     cycle, it informs the central computer that it is available again.
  The central computer has access to the same information shared by the stations and executes the following pseudo-code to release machines: <br>
  
    void release(int machine) /* Releases machine */
    {
      available[machine] = TRUE;
      V(nfree);
    } 
  
  The available array is initialized to all true, and the semaphore nfree is initialized to NMACHINES.
  Model such an asynchronous system and verify the properties of interest for the success of the laundromat.
  </li>
</ul>

