Imports
	ADVAPI32
		GetUserNameA
	KERNEL32
		AllocConsole
		GetCommandLineA
		GetComputerNameA
		GetCurrentDirectoryA
	USER32
		FindWindowA
		ShowWindow
	WS2_32
		closesocket
		connect
		htons
		inet_addr
Functions
Exports
Strings
	"CRT"
	"libgcc"



entry
	_mainCRTStartup
		_main
			HWND
			AllocConsole
			hWnd = FindWindowA
			ShowWindow(hWnd,1)
			disclaimer(1)
			revshell()
				ReverseShellSetup
					WSAStarup
					tcpsock
					sockaddr
					htons
					my_conn
						closesocket
						WSACleanup
						exit(0)
				whoami - (recv_buff == whoami)
					Returns_GetUserNameA(lpBuffer)
					send(lpBuffer)
					memset(recv_buff)
				pwd - (recv_buff == pwd)
					Returns_GetCurrentDirectoryA(lpBuffer)
					send(lpBuffer)
					memset(recv_buff)
				hostname (recv_buff == hostname)
					Returns_GetComputerNameA(lpBuffer)
					send(lpBuffer)
					memset(recv_buff)
				exit - (recv_buff == exit)
					closesocket
					WSACleanup
					exit(0)
				else "Invalid Command"
					send(&InvalidCommand)
					memset(recv_buff)
