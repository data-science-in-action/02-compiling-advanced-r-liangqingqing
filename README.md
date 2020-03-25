# 02-compiling-advanced-r-liangqingqing
title: "Problems and Solutions to Build the Book Advanced R Programming using Rstudio"
author: "liangqingqing"
date: "2020/3/25"
output: pdf_document

During the building process,i have met some problems,What is shown below is my problems and its solutions.

1.processing file: Introduction.Rmd
����̼�����'dplyr'
The following objects are masked from 'package:stats':
    filter, lag
The following objects are masked from 'package:base':
    intersect, setdiff, setequal, union
solution :stats::filter
          stats::lag
		  base::intersect
		  base::setdiff
		  base::setequal
		  base::union

2.Quitting from lines 223-235 (Introduction.Rmd)
solution :Adding'encoding = "UTF-8"' in line 224 can fix it.
    then:contributors <- read.csv("contributors.csv", stringsAsFactors = FALSE,encoding = "UTF-8")

3.	Quitting from lines 96-103 (Functionals.Rmd) 
Error in loadNamespace(name) : 不存在叫'emo'这个名字的程辑包
Calls: local ... loadNamespace -> withRestarts -> withOneRestart -> doWithOneRestart
I tried these methods.
I first install emo with install.package, but it gives a warning message
                  Warning in install.packages :
                         package ‘emo’ is not available (for R version 3.6.3)
Then I install the package from Hadley's github.com by
                  install.packages("devtools")
				  devtools::install_github("hadley/emo")
but it gave a message:
        package ‘glue’ successfully unpacked and MD5 sums checked
        错误: Failed to install 'emo' from GitHub:
          (由警告转换成)cannot remove prior installation of package ‘glue’
I trid again.
         Error in file.copy(lp, dirname(pkgdir), recursive = TRUE, copy.date = TRUE) : 
        (由警告转换成)拷贝D:\R\R-3.6.3\library\00LOCK-Rcpp\Rcpp\libs\i386\Rcpp.dll到D:\R\R-3.6.3\library\Rcpp\libs\i386\Rcpp.dll时出了问题：Permission denied 
         * removing 'D:/R/R-3.6.3/library/Rcpp'
         * restoring previous 'D:/R/R-3.6.3/library/Rcpp'
         Error in file.copy(lp, dirname(pkgdir), recursive = TRUE, copy.date = TRUE) : 
         (由警告转换成)拷贝D:\R\R-3.6.3\library\00LOCK-Rcpp\Rcpp\libs\i386\Rcpp.dll到D:\R\R-3.6.3\library\Rcpp\libs\i386\Rcpp.dll时出了问题：Permission denied 
         停止执行
         错误: Failed to install 'unknown package' from GitHub:
         (由警告转换成)installation of package ‘Rcpp’ had non-zero exit status 
I met a new problem when i opened it again.
	     Error:package"Rcpp"does not have a have a namespace
solution: First,I removed the "RCPP",then continuing these steps.
          install.packages("Rcpp")
          devtools::install_github("hadley/sloop",force = TRUE)
		  devtools::install_github("hadley/emo")

4.Warning message:
          In system(cmd) : 'make' not found
          Quitting from lines 77-84 (Rcpp.Rmd)
solution:I download Rtools.Then I added C:\Rtools\bin\ to the path of the environment variable of the computer system, but the error still occurred, so I reinstalled Rtools 
      and successfully solved this problem.

5.Missing Packages：
solution:Most of the warnings are about packages missing. The packages I installed during the process are glue, lubridate, purr, DBI, RSQLite, zeallot, Rcpp, tinytex, dbplyr, profris ,bench etc.

6.xelatex.exe GUI framework cannot be initiallized or xelatex not found
solution:I download the MiKTeX from the internet .Then I clicked the setting in the MiKTeX,which choosing the item of 'always install...'

7.Error: Package fontspec Error: The font "Inconsolata" cannot be found
solution:I downloaded the font 'Inconsolate' from the internet, and put it to C:\Windows\Fonts.

Finally,this book was successfully built . I thank my classmates for helping me .