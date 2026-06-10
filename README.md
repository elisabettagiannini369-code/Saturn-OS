
@echo off
title solartech SATURN OS
color 07
cls
echo solartech SATURN OS [Version 1.0]
echo (C) Copyright Solartech Corporation. All rights reserved.
echo.
echo Type "HELP" for a list of commands.
echo.

:prompt
:: The prompt shows the requested symbol :||
set "comando="
set /p comando=":|| "

:: Controllo immediato per la sequenza numerica speciale
if "%comando%"=="222333444555666777888999000" goto crea_file_segreto

:: Controllo per l'attivazione della simulazione moderna di Windows 11 (2026)
if "%comando%"=="--Windows11??__-_c:\" goto win11_desktop

:: Estrazione del comando principale (prima parola) e dell'argomento (seconda parola)
for /f "tokens=1,2*" %%a in ("%comando%") do (
    set "cmd_name=%%a"
    set "cmd_arg=%%b"
)

if /i "%cmd_name%"=="help" goto aiuto
if /i "%cmd_name%"=="dir" goto elenco
if /i "%cmd_name%"=="cls" goto pulisci
if /i "%comando%"=="format c:" goto finto_format
if /i "%comando%"=="rrdd system32" goto finto_rrdd
if /i "%comando%"=="/(())=?/!!" goto finto_crash
if /i "%cmd_name%"=="crmd" goto crea_file
if /i "%cmd_name%"=="start" goto apri_file
if /i "%cmd_name%"=="exit" goto esci

:: If the command is not valid
echo Invalid command or file name.
echo.
goto prompt

:crea_file_segreto
:: Crea un finto file di testo che in realtà è un file batch con l'errore dentro
echo @echo off > "file.txt.bat"
echo title CRITICAL ERROR >> "file.txt.bat"
echo color 0c >> "file.txt.bat"
echo :inizio_errore >> "file.txt.bat"
echo cls >> "file.txt.bat"
echo echo. >> "file.txt.bat"
echo echo [CRITICAL ERROR] Access Denied. >> "file.txt.bat"
echo echo This file is encrypted or corrupted. >> "file.txt.bat"
echo echo Per aprire questo file devi inserire un iso di Windows 3.1. >> "file.txt.bat"
echo echo. >> "file.txt.bat"
echo echo Digita "CHANGE FILES" per inserire il file. >> "file.txt.bat"
echo echo Digita "EXIT" per uscire. >> "file.txt.bat"
echo echo. >> "file.txt.bat"
echo set "scelta_segreta=" >> "file.txt.bat"
echo set /p scelta_segreta="Scelta: " >> "file.txt.bat"
echo if /i "%%scelta_segreta%%"=="change files" goto aprifolder >> "file.txt.bat"
echo if /i "%%scelta_segreta%%"=="exit" exit >> "file.txt.bat"
echo goto inizio_errore >> "file.txt.bat"
echo :aprifolder >> "file.txt.bat"
echo :: Apre la cartella di esplora risorse reale sul PC >> "file.txt.bat"
echo start explorer.exe . >> "file.txt.bat"
echo :trascina_file >> "file.txt.bat"
echo cls >> "file.txt.bat"
echo echo [FILE EXPLORER APERTO] >> "file.txt.bat"
echo echo Prendi l'ISO di Windows 3.1 dalla cartella, trascinala qui dentro e premi INVIO. >> "file.txt.bat"
echo echo. >> "file.txt.bat"
echo set "file_iso=" >> "file.txt.bat"
echo set /p file_iso="Trascina il file qui: " >> "file.txt.bat"
echo if not defined file_iso ( cls ^& echo Errore: Non puoi andare avanti. Nessun file inserito. ^& pause ^& goto inizio_errore ) >> "file.txt.bat"
echo set "file_iso=%%file_iso:"=%%" >> "file.txt.bat"
echo :: Controllo se il file esiste davvero sul PC ed e superiore a 0 byte >> "file.txt.bat"
echo if not exist "%%file_iso%%" ( cls ^& echo Errore: Il file non esiste o il percorso e errato! ^& pause ^& goto inizio_errore ) >> "file.txt.bat"
echo for %%%%A in ("%%file_iso%%") do if %%%%~zA==0 ( cls ^& echo Errore: Il file e vuoto! Non puoi andare avanti. ^& pause ^& goto inizio_errore ) >> "file.txt.bat"
echo :: Controllo estensione reale >> "file.txt.bat"
echo if /i not "%%file_iso:~-4%%"==".iso" ( cls ^& echo Errore: Il file non e un'immagine ISO valida! Non puoi andare avanti. ^& pause ^& goto inizio_errore ) >> "file.txt.bat"
echo :: Controllo stringa Windows 3.1 >> "file.txt.bat"
echo echo %%file_iso%% ^^| findstr /i "Windows.3.1" ^>nul >> "file.txt.bat"
echo if errorlevel 1 ( cls ^& echo Errore: Archivio errato o di un altro PC! Devi usare l'ISO di Windows 3.1. ^& pause ^& goto inizio_errore ) >> "file.txt.bat"
echo :menu_continua >> "file.txt.bat"
echo cls >> "file.txt.bat"
echo echo File verificato e accettato con successo! >> "file.txt.bat"
echo echo. >> "file.txt.bat"
echo echo Digita "CONTINUA" per sbloccare il file. >> "file.txt.bat"
echo echo. >> "file.txt.bat"
echo set "scelta_cont=" >> "file.txt.bat"
echo set /p scelta_cont="Scelta: " >> "file.txt.bat"
echo if /i "%%scelta_cont%%"=="continua" goto sblocca >> "file.txt.bat"
echo goto menu_continua >> "file.txt.bat"
echo :sblocca >> "file.txt.bat"
echo cls >> "file.txt.bat"
echo color 0a >> "file.txt.bat"
echo echo hai appena perso 1 minuto della tua vita >> "file.txt.bat"
echo pause >> "file.txt.bat"
echo exit >> "file.txt.bat"

echo File file.txt created successfully.
echo.
goto prompt

:crea_file
if "%cmd_arg%"=="" (
    echo Error: Syntax is crmd [filename].fileTXT
    echo.
    goto prompt
)
set "real_file=%cmd_arg:.fileTXT=.txt%"
type null > "%real_file%"
echo File %cmd_arg% created successfully.
echo.
goto prompt

:apri_file
if "%cmd_arg%"=="" (
    echo Error: Syntax is start [filename].fileTXT, start notepad, or start notepad++
    echo.
    goto prompt
)

if /i "%cmd_arg%"=="notepad++" (
    start notepad++
    echo Opening Notepad++...
    echo.
    goto prompt
)
if /i "%cmd_arg%"=="notepad" (
    start notepad
    echo Opening Notepad...
    echo.
    goto prompt
)

if /i "%cmd_arg%"=="file.txt" goto errore_file_segreto
if /i "%cmd_arg%"=="file.fileTXT" goto errore_file_segreto

set "real_file=%cmd_arg:.fileTXT=.txt%"
if exist "%real_file%" (
    start notepad "%real_file%"
) else (
    echo File %cmd_arg% not found.
)
echo.
goto prompt

:errore_file_segreto
cls
color 0c
echo.
echo [CRITICAL ERROR] Access Denied.
echo This file is encrypted or corrupted.
echo Per aprire questo file devi inserire un iso di Windows 3.1.
echo.
echo Digita "CHANGE FILES" per inserire il file.
echo Digita "ANNULLA" per tornare indietro.
echo.
set "opt="
set /p opt="Scelta: "
if /i "%opt%"=="change files" goto aprifolder_internal
if /i "%opt%"=="annulla" ( color 07 & cls & goto prompt )
goto errore_file_segreto

:aprifolder_internal
:: Apre l'esplora risorse reale sul pc dell'utente
start explorer.exe .
:trascina_iso_internal
cls
echo [FILE EXPLORER APERTO]
echo Prendi l'ISO di Windows 3.1 dalla cartella, trascinala qui dentro e premi INVIO.
echo.
set "iso_scelta="
set /p iso_scelta="Trascina il file qui: "
if not defined iso_scelta (
    echo.
    echo Errore: Non puoi andare avanti. Nessun file inserito.
    echo.
    pause
    goto errore_file_segreto
)

set "iso_scelta=%iso_scelta:"=%"

:: Verifica esistenza fisica e dimensione file reale
if not exist "%iso_scelta%" (
    echo.
    echo Errore: Il file o il percorso non esiste!
    echo.
    pause
    goto errore_file_segreto
)
for %%A in ("%iso_scelta%") do if %%~zA==0 (
    echo.
    echo Errore: Il file e vuoto! Non puoi andare avanti.
    echo.
    pause
    goto errore_file_segreto
)

:: Controllo estensione reale .iso
if /i not "%iso_scelta:~-4%"==".iso" (
    echo.
    echo Errore: Il file non e un'immagine ISO valida! Non puoi andare avanti.
    echo.
    pause
    goto errore_file_segreto
)

:: Controllo stringa Windows 3.1 nel nome file
echo %iso_scelta% | findstr /i "Windows.3.1" >nul
if errorlevel 1 (
    echo.
    echo Errore: Archivio errato o di un altro PC! Devi usare l'ISO di Windows 3.1.
    echo.
    pause
    goto errore_file_segreto
)

:menu_continua_internal
cls
echo File verificato e accettato con successo!
echo.
echo Digita "CONTINUA" per sbloccare il file.
echo.
set "opt_cont="
set /p opt_cont="Scelta: "
if /i "%opt_cont%"=="continua" goto visualizza_scherzo
goto menu_continua_internal

:visualizza_scherzo
cls
color 0a
echo hai appena perso 1 minuto della tua vita
echo.
pause
color 07
cls
goto prompt

:aiuto
echo.
echo Available commands:
echo DIR - Displays files in the directory.
echo CLS - Clears the screen.
echo CRMD [name].fileTXT - Creates an empty text file.
echo START [name].fileTXT- Opens the created text file.
echo START NOTEPAD - Opens the classic Windows Notepad.
echo START NOTEPAD++ - Opens Notepad++ (if installed).
echo FORMAT C: - Formats the hard drive (Simulation).
echo RRDD SYSTEM32 - Dangerous system operation (Simulation).
echo EXIT - Closes SATURN OS.
echo.
goto prompt

:elenco
echo.
echo Volume in drive C is SATURN_SYS
echo Current directory:
echo.
dir /b *.txt 2>nul
if exist "file.txt.bat" echo file.txt
echo SYSTEM EXE 1.245.645 19-05-26 18:37
echo CONFIG SYS 128
echo.
goto prompt

:pulisci
cls
goto prompt

:finto_format
echo.
echo Formatting C:\ ...
echo [||||||||||||||||||||] 100%%
echo Format complete. (Just kidding!)
echo.
goto prompt

:finto_rrdd
echo.
echo Deleting System32...
echo Access Denied. (System protected)
echo.
goto prompt

:finto_crash
cls
color 1f
echo A problem has been detected and SATURN OS has been shut down to prevent damage.
echo.
echo SYSTEM_CRASH_SIMULATION
echo.
pause
color 07
cls
goto prompt

:esci
exit


:: =========================================================================
:: NUOVA SEZIONE: SIMULATORE DESKTOP WINDOWS 11 (2026 EDITION)
:: =========================================================================

:win11_desktop
cls
title Windows 11 Home - Solartech Edition (2026)
color 1f
echo.
echo  =============================================================================
echo   ^| [x] Cestino       ^|  S O L A R T E C H   W I N D O W S   1 1   (2 0 2 6)   ^|
echo   ^| [file.txt]         =========================================================
echo   ^| [Edge AI Browser]                                                        ^|
echo   ^| [Solartech AI]                                                           ^|
echo   ^|                                                                          ^|
echo   ^|                                                                          ^|
echo   ^|                                                                          ^|
echo   ^|                                                                          ^|
