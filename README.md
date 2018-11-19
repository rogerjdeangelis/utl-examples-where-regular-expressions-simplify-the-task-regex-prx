# utl-examples-where-regular-expressions-simplify-the-task-regex-prx
Examples where regular expressions simplify the task regex prx.

    Examples where regular expressions simplify the task regex prx

    I try to use basic SAS string operation however there are
    instances when regular expresions simplify the task.

    Examples where regular expressions are needed prx regex

      Three Examples

          1. Count of 'booboo' in 'boobooboobooboo' should be 2
          2. Text in common if prxmatch('/MAY|STEVE/',"ROGER MAY PENG")>0
          3. Valid SSN (or email..)


    PROCESS
    =======

    1. Distinct Count of 'booboo' in 'boobooboobooboo' should be 2
    ---------------------------------------------------------------

       data _null_ ;
           s='boobooboobooboo';
          cnt=countc(prxchange('s/([booboo]){6}/*/',-1,s),'*') ;
          put cnt= ;
       run;quit;

       CNT=2

         1       2    NO
       booboo booboo boo


    2. Text in common if prxmatch('/MAY|STEVE/',"ROGER MAY PENG")>0
    ----------------------------------------------------------------

       data _null_ ;
          if prxmatch('/MAY|STEVE/',"ROGER MAY PENG")>0 then put 'MAY is in both strings';
       run;quit;

       MAY is in both strings


    3 Valid SSN  (SSNs cannot begin with 666 reserved for Satan)
    ------------------------------------------------------------

       data _null_;

         ssn='321-54-9876';
         *lost the reference?
         if prxmatch('/^(?!000)(?!666)(?!9)\d{3}([- ]?)(?!00)\d{2}\1(?!0000)\d{4}$/'
          ,ssn)>0 then put "Valid";

       run;quit;

       This does not match all the rules in
       http://en.wikipedia.org/wiki/Social_Security_number#Valid_SSNs

