# utl-sorting-the-roots-of-a-polynomial-in-ascending-order-of-the-imaginary-part
Sorting the roots of a polynomial in ascending order of the imaginary part.

    Sorting the roots of a polynomial in acsending order of the imaginary part

    github
    https://tinyurl.com/y9em44x6
    https://github.com/rogerjdeangelis/utl-sorting-the-roots-of-a-polynomial-in-ascending-order-of-the-imaginary-part

    StackOverflow
    https://tinyurl.com/y6vzw6jb
    https://stackoverflow.com/questions/52518107/sorting-a-complex-vector-by-imaginary-part-in-r

    Profile
    https://stackoverflow.com/users/4891738/%E6%9D%8E%E5%93%B2%E6%BA%90


    INPUT
    =====

       I want the roots of this polnonmial in ascending order by the imaginary part

       0 = 1 +  2x +  3x**2 + 4x**3 + 5x**4


       %let coef=%str(1, 2, 3, 4, 5);


    EXAMPLE OUTPUT
    --------------
     WORK.WANT total obs=4

      Obs         LOW2HI           |  RULES
                                   |
       1    0.1378323 -0.6781544i  |  In acsending order by the imaginary part
       2   -0.5378323 -0.3582847i  |
       3   -0.5378323 +0.3582847i  |
       4    0.1378323 +0.6781544i  |


    PROCESS
    ========

    %utl_submit_r64("
    roots <- polyroot(c(&coef));
    Im(roots);
    root<-paste0(format(roots[order(Im(roots))]));
    root<-paste(root, sep = ' ', collapse = ' ');
    root;
    writeClipboard(root);
    ",returnvar=root);

    %put &=root;

    data want;
      retain root "&root";
      do ix=1 to countc(root," ");
        low2hi = scan(root,ix," ");
        output;
      end;
      drop root ix;
    run;quit;


    OUTPUT
    ======

     see above

    *                _               _       _
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|

    ;

     %let coef=%str(5, 4, 3, 2, 1);



