```CD:

cd 								--> working
cd .. 							--> working
cd . 							--> working
cd /Users 						--> working
cd // 							--> working
cd '//' 						--> working
cd ////// 						--> working
cd ./././ 						--> working
cd / 							--> working
cd '/etc' 						--> working
cd '/var' 						--> working
cd "$PWD/prompt"				--> working
cd "doesntexist"				--> working
cd "doesntexist" 2>/dev/null	--> working
cd ../../..						--> working
cd ..							--> working
cd ..							--> working
cd ?							--> working
cd +							--> working
cd _							--> working
cd bark bark					--> working
cd '/'							--> working
cd $PWD/file_tests				--> working
cd $OLDPWD/builtins				--> working

ECHO:

echo																--> working
echo echo															--> working
eCho																--> working
eChO																--> working
eCHO																--> working
echo $																--> working
echo $ $															--> working
ECHO																--> working
echo rhobebou														--> working
echo stop barking													--> working
echo "bonjour"														--> working
echo bonjour														--> working
echo 'bonjour'														--> working
echo -n bonjour														--> working
echo -nn bonjour													--> working
echo -n -n -n bonjour												--> working
echo "-n" bonjour													--> working
echo -n"-n" bonjour													--> working
echo "-nnnn" bonjour												--> working
echo "-nnnn" -n bonjour												--> working
echo "-n -n -n"-n bonjour											--> working
echo "-n '-n'" bonjour												--> working
echo $USER															--> working
echo "$USER"														--> working
echo "'$USER'"														--> working
echo " '$USER' "													--> working
echo text"$USER"													--> working
echo text"'$USER'" ' $USER '										--> working
echo "text"   "$USER"    "$USER"									--> working
echo '              $USER          '								--> working
echo               text "$USER"            "$USER"text				--> working
echo ''''''''''$USER''''''''''										--> working
echo """"""""$USER""""""""											--> working
echo $USER'$USER'text oui oui     oui  oui $USER oui      $USER ''	--> working
echo $USER '' $USER $USER '' $USER '' $USER -n $USER				--> working
echo ' \' ' \'														--> NOT WORKING! (remove quotes)
echo '\" ' " \"\""													--> NOT WORKING! (remove quotes)
echo \\\" \\\" \\\" \\\"\\\"\\\" \\\'\\\'\\\'						--> NOT WORKING! (remove quotes)
echo "$USER""$USER""$USER"											--> working
echo text"$USER"test												--> working
echo '$USER' "$USER" "text \' text"									--> working
echo '$USER'														--> working
echo $USER " "														--> working
echo "$USER""Users/$USER/file""'$USER'"'$USER'						--> working
echo "$USER$USER$USER"												--> working
echo '$USER'"$USER"'$USER'											--> working
echo '"$USER"''$USER'"""$USER"										--> working
echo " $USER  "'$PWD'												--> working
echo " $USER  \$ "'$PWD'											--> working
echo $USER=4														--> working
echo $USER=thallard 												--> working
echo $USER															--> working
echo $?																--> working
echo $PWD/file														--> working
echo "$PWD/file"													--> working
echo "text" "text$USER" ... "$USER"									--> working
echo $PWD															--> working

EXIT:

exit 0 0															--> working
exit 42 42															--> working
exit -42 -24														--> working
exit 42																--> working
exit 42 53 68														--> working
exit 259															--> working
exit -12030															--> working
exit --1239312														--> working
exit ++++1203020103													--> working
exit +0																--> working
exit ++++++0														--> NOT WORING!
exit -----0															--> NOT WORING!
exit azerty															--> working
exit kewkwqke														--> working
exit a																--> working
exit z																--> working
exit "1"															--> working
exit "2"															--> working
exit "+102"															--> working
exit "1230"															--> working
exit "+++1230"
exit "1"23															--> working
exit "2"32"32"
exit "'42'"															--> working
exit '42'"42"42
exit +'42'"42"42
exit -'42'"42"42
exit 9223372036854775807 											--> working
exit 9223372036854775808
exit -4																--> working
exit 1																--> working
exit -1																--> working
exit 42																--> working
exit 0																--> working
exit --000															--> working
exit +++++++000														--> working
exit ++++3193912939													--> working
exit ---31232103012													--> working
exit "something"													--> working
exit echo															--> working
exit cd ..															--> working
exit 0 0															--> working
exit 42 42 42 42 42													--> working
exit echo something													--> working
exit exit															--> working

EXPORT:

env | grep "_="														--> working
export | grep "SHLVL"												--> working
export | grep "OLDPWD"												--> working
export | grep "PWD"													--> working
export $?															--> working
export TEST															--> working
export TEST=														--> working
export TEST=123														--> working
export ___TEST=123													--> working
export --TEST=123													--> working
export ""=""														--> working
export ''=''														--> working
export "="="="														--> working
export '='='='														--> working
export TE\\\ST=100													--> working
export TE-ST=100													--> working
export -TEST=100													--> working
export TEST-=100													--> working
export _TEST=100													--> working
export TEST															--> working
export ==========													--> working
export 1TEST=														--> working
export TEST															--> working
export ""=""														--> working
export TES=T=""														--> working
export TE+S=T=""													--> working
export TES\\\\T=123
export TES.T=123
export TES\\\$T=123
export TES\\\\T
export TES.T=123
export TES+T=123
export TES=T=123
export TES}T=123
export TES{T=123
export TES-T=123
export -TEST=123
export _TEST=123
export TES_T=123
export TEST_=123
export TE*ST=123
export TES#T=123
export TES@T=123
export TES!T=123
export TES$?T=123
export =============123
export +++++++=123
export ________=123
export export
export echo
export pwd
export cd
export export
export unset
export sudo
export TES^T=123
export TES!T=123
export TES\~T=123
export TEST+=100

PIPES:

env | grep "_="																--> working
env | grep "SHLVL"															--> working
echo oui | cat -e															--> working
echo oui | echo non | echo something | grep oui								--> working
echo oui | echo non | echo something | grep non								--> working
echo oui | echo non | echo something | grep something						--> working
cd .. | echo "something"													--> working
cd .. | echo "something"													--> working
cd / | echo "something"														--> working
cd .. | pwd																	--> working
ifconfig | grep ":"															--> working
ifconfig | grep nothing														--> working
whoami | grep $USER															--> working
whoami | grep $USER > tmp/file												--> working
whoami | cat -e | cat -e > tmp/file											--> working
cat Makefile | grep "FLAGS"													--> working
cat Makefile | cat -e | cat -e												--> working
cat Makefile | grep "FLAGS" | grep "FLAGS" | cat -e							--> working
export TEST=123 | cat -e | cat -e											--> working
unset TEST | cat -e															--> working
echo test | cat -e | cat -e | cat -e										--> working
whereis ls | cat -e | cat -e > test											--> working
echo test | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e | cat -e
ls -la | grep "."															--> working
whereis grep > tmp/file														--> working
whereis grep > tmp/file														--> working
ls -la > tmp/file															--> working
ls -la > tmp/file															--> working

UNSET:

unset
export TEST=100
unset doesntexist
unset PWD
unset PWD
unset OLDPWD
unset PATH
unset PATH
unset PATH
unset TES\\\\T
unset TES;T
unset TES.T
unset TES+T
unset TES=T
unset TES}T
unset TES{T
unset TES-T
unset -TEST
unset _TEST
unset TES_T
unset TEST_
unset TE*ST
unset TES#T
unset TES@T
unset TES!T
unset TES$?T
unset ============
unset +++++++
unset ________
unset export
unset echo
unset pwd
unset cd
unset unset
unset sudo
unset TES^T
unset TES!T
unset TES\~T
8:20
<in cmd "str1 str2 str3" | cmd2 -arg | cmd3 >out >out2
cmd "str1 str2 str3" >out | cmd2 -arg | cmd3 >out2 >out3
cmd "str1 str2 str3" >out | cmd2 -arg str | cmd3 str >out2 >out3
cmd <in -arg | cmd2 "str |" >out>>out2
cmd1 <in1 -arg1 > out1 | cmd2 <in2 -arg2 > out2


echo $PWD
echo $PWD|cat -e
echo $PWD hallo | cat -e
echo '$PWD hallo | cat -e'
echo "$PWD hallo | cat -e"


export TEST=1 test=2 sup=																--> working
export TEST=1 test=2 sup= | env															--> working


wc < Makefile -l | cat -e > outfile | echo hello | rev > outfile2						--> working

< test.txt < Makefile<README.md wc -l|cat -e | rev										--> working

< Makefile cat > out | < README.md cat -e 												--> working
< README.md cat -e | <Makefile cat														--> working

< in1 cat -e | < in2 cat																--> working
< in1 cat -e > out1 | < in2 cat															--> working

env | rev | head -5 | cat -e | rev														--> working
< in1 <in2 <in3 < Makefile rev | head -5 | cat -e | rev > out > out2 > out3 >> out4		--> working

echo ok"hello"ok1"mfg" == echo ok'hello'ok1'mfg'
-- okhellook1mfg

echo okhellook1"mfg" == echo okhellook1'mfg'
-- okhellook1mfg

echo "o""k       "hellook1 == echo 'o''k       'hellook1
-- ok       hellook1

echo '"***hello***"'
"***hello***"

echo "'***hello***'"
"***hello***'

echo ok"'hello'"ok1"hello1"ok2

echo "text"   "$USER"    "$USER"
echo """"""""$USER""""""""
echo "-n -n -n"-n bonjour
echo "'$USER'"
< in1 < in2																				--> working
< in1 cat < in2																			--> working
< Makefile > outfile																	--> working
> out																					--> working


echo "$PWD         "a
/Users/wollio/Desktop/projects/4/minishell         a

echo "         $PWD"
         /Users/wollio/Desktop/projects/4/minishell
```


echo "Starting test" | tee >(mkdir -p test_dir) >(cd test_dir 2>/dev/null || true) | cat | grep "Starting" | tee >(echo "Hello World" > test_dir/file1.txt) | cat | tee >(echo "Another line" >> test_dir/file1.txt) | tee >(cat test_dir/file1.txt | grep "Hello" | wc -l > test_dir/results.txt) | tee >(export TEST_VAR="test_value") | tee >(echo $TEST_VAR | tr 'a-z' 'A-Z' >> test_dir/results.txt) | tee >(ls -la /usr/bin | grep "^-..x..x..x" | head -n 5 >> test_dir/results.txt) | tee >((echo "Command in subshell" | cat - <(date "+%Y-%m-%d")) >> test_dir/results.txt) | tee >(touch test_dir/file{1..5}.tmp) | tee >(echo "Created: $(ls test_dir/*.tmp | wc -l) temporary files" >> test_dir/results.txt) | tee >(find test_dir -name "*.txt" -type f -exec cat {} \; | sort | uniq > test_dir/sorted_output.txt) | tee >(echo 'Single quoted $TEST_VAR' >> test_dir/results.txt) | tee >(echo "Double quoted $TEST_VAR" >> test_dir/results.txt) | tee >(echo "Current path is $PWD" >> test_dir/results.txt) | cat test_dir/results.txt | tee >(rm -rf test_dir)
