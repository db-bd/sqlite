### SQLite Database Manipulation from C Program

#### Download DLL From [https://sqlite.org/](https://sqlite.org/download.html)

* Download SQLite Source Code which contains sqliteX.h File [ X Means SQLite Version ]
* Download 32 Bit DLL or 64 Bit DLL
* Say Visual Studio Project is 32 Bit Version so we Download 32 Bit version of DLL
* Navigate to DLL Directory
* Run Following Command & Create sqliteX.lib 
  ```sh
  lib /DEF:sqlite3.def /OUT:sqlite3.lib /MACHINE:x86 [32 Bit]
  lib /DEF:sqlite3.def /OUT:sqlite3.lib /MACHINE:x64 [64 Bit]
  ````
* Like Any Other C/C++ Library Using in Visual Studio
* Header Files Including
```sh
  Project Properties -> Configuration Properties -> VC++ Directories -> Include Directories -> sqliteX.h Containing Folder
```
* Library Files Including
```sh
  Project Properties -> Configuration Properties -> VC++ Directories -> Library Directories -> sqliteX.lib Containing Folder
```
* Library Files Linking
```sh
  Project Properties -> Configuration Properties -> Linker -> Input -> Additional Dependencies -> sqlite3.lib
```
* Copy sqlite3.dll to Project Debug Folder Where Binary is Created
* Congratulation You have successfully Created Project Environment

#### Run a Test Code
```c
#include <stdio.h>
#include <sqlite3.h> 

int main(int argc, char* argv[]) {
	sqlite3 *db;
	char *zErrMsg = 0;
	int rc;

	rc = sqlite3_open("test.db", &db);

	if (rc) {
		fprintf(stderr, "Can't open database: %s\n", sqlite3_errmsg(db));
		return(0);
	}
	else {
		fprintf(stderr, "Opened database successfully\n");
	}
	sqlite3_close(db);
}
```
