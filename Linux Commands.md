# Linux Commands

#### Basic

- `pwd` : print working (current) directory
- `clear`: clear terminal screen

#### Change Directory (`cd`)

Change directory to location specified in options

- `cd` (no options) : go to home directory
- `cd /` : go to root
- `cd ~` : go to home directory of current user
- `cd ~user1` : go to home directory of user 'user1'
- `cd ~-` : go to previous directory

#### List Segment (ls)

현재 디렉토리의 목록 보여주기

- `ls /a/ /b/` : show files/directories of both `/a/` and `/b/`
- `ls -a` : 모든 목록 보여주기
  - .(숨김)을 포함한 디렉토리 안의 모든 파일&디렉토리 출력
  - does not differentiate between files and directories
- `ls -l` : 목록을 자세히 보여주기
  - commonly referred to as `ll` (alias)
  - e.g) `ls -l /home/jiwon/a/` : a 디렉토리 안에 있는 목록을 자세히 보여주기
- `ls -al` : 숨김 파일을 포함한 모든 목록을 자세히 보여주기
  - 다른 옵션도 중첩 가능 (e.g `-na`)
- `ls -n` : 파일 및 디렉토리 정보 출력 시 UID, GID (소유권 사용) - display UID, GID
- `ls -R` : 하위 경로와 그 안에 있는 모든 파일들도 같이 출력
- `ls -F` : 형식을 알리는 문자를 각 파일/디렉토리 이름 뒤에 추가
  - (nothing appended): file
    - Access Permissions begin with `-`
  - `->`, `@` : symbolic link file (shortcut/alias)
    - 사본 `->` 원본
    - Access Permissions begin with `l`
    - 허가권 다 활성화
  - `*` : 실행파일
- `ls -lh` : shows sizes in human readable format
  - e.g) 1855 => 1.9K
- `ls -d` : directory 정보 출력 (usually to check if a specific directory exists)
- `ll -d` : display extended directory info (including permission, UID, GID, date created, etc.)

#### Make/Remove Directory

- `mkdir` : make directory
  - 맨 마지막에 오는 디렉토리 위치가 대상이 된다.
  - `a`까지 있고 `b`라는 디렉토리가 없는 상태에서 `mkdir ./a/b/c/` 하면 (`c`라는 디렉토리를 생성하라고 명령하면) 에러가 뜬다.
- `mkdir -p` : 하위 디렉토리 생성 시, 상위 디렉토리가 없으면 상위 디렉토리도 함께 생성한다
  -  `a`까지 있고 `b`라는 디렉토리가 없는 상태에서 `mkdir ./a/b/c/`  하면 `b`, `c` 둘 다 생성
- `rmdir` : delete (empty) directory
- `rmdir -p` : 디렉토리 삭제 시, 지정한 최상위 디렉토리까지 삭제 시도 (단, 비어 있는 디렉토리만 삭제)

#### Delete, Copy, Move

- `rm` : delete files and directories with files in it (enter 'yes', 'ye', or 'y' to confirm)
  - by default, option `-i` is included : prompt user before every removal
  - no options (except `-i`): delete files only
- `rm -f` : ignore prompts (+ hides any error messages)
- `rm -r` : recursively deletes all directories and files (including child contents)
  - first asks to descend into child directory
  - e.g) `rm -rf ./*` : deletes all files and directories in the current directory without prompting the user
  - e.g) `rm -rf /*` : deletes the entire server
- `cp` : copy files and/or directories
  - `cp [-option] [source] [source] ... [source] [target]`
    - may change name of file to be copied
    - may copy multiple sources with 1 command line
    - wild card `*` : refers to all files in specified directory
  - e.g) `cp /etc/inittab /backup/` : copy `inittab` into `/backup/`
  - e.g) `cp /test/* ./a/` : copy all files in `/test/` into `./a/`
- `cp -r` : recursively copy directory and all child files/directories in it
- `mv` : move (cut and then paste)
  - no options
  - usage is essentially the same as the `cp` command
  - file name change is also possible, but time created will remain the same
    - e.g) `mv /backup/login /backup/login.defs`

#### Touch

- `touch` : create new empty files or change created date for existing files
  - `touch -t YYYYMMDDHHmm fileOrDirectory`
    - designate date and time (up to minutes)
  - `touch -d YYYYMMDD fileOrDirectory`
    - designate up to date
  - if `fileOrDirectory` does not already exist, create a new empty file under that name
  - but if `fileOrDirectory` already exists, only change the created date for that file
    - no options : use current date and time
    - use options to designate specific date and time

#### Alias

- `alias` : create shortcut
  - e.g) `alias 1='clear'`, `cp='cp -i'`
- `unalias` : disable shortcut
  - e.g) `unalias 1`

#### Print file content

- `head -[n]` : print first _n_ lines of file (default: 10 lines)
- `tail -[n]` : print last _n_ lines of file (default: 10 lines)
- `more` : 화면 단위로 출력
  - Ctrl + Enter => 1 more line
  - Ctrl + Spacebar => 1 more page
  - cannot view previous lines/pages
  - cannot print directory content (only file content)
- `less` : [program] use `J` and `K` to move up or down
  - press `Q` to escape
- `nl` : number each line
  - e.g) `ls -l /etc/ | nl` : number each line when printing `ls -l /etc/`

#### Pipe

- combine multiple commands in a single line
  - e.g) `ls -l /etc/ | nl | more | less`
  - e.g) `ls -l /etc/ | nl | less | more`