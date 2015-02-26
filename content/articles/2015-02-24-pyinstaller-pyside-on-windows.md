Title: Python na Windows bez Pythonu?
Category: External memory
Tags: python, pyside, windows, pyinstaller
Authors: Věroš Kaplan
Summary: 
    Je možné spustit program v Pythonu na Windows bez instalovaného Pythonu? 
    Je možné zabalit aplikace v Pythonu do .EXE soubor? 
    Je!
Slug: pyinstaller-python-apps-on-windows-without-python
Language: cz

Pro neziskovku ([mateřské centrum][matata]) - jsem vyráběl malý program v Pythonu 
v PySide GUI. Jenže neziskovka má počítače na Windows a můj vývojářský stroj 
je na Linuxu. A nutit maminky instalovat do náhodného počítače Python 
pro Windows včetně knihovně je ... *moc práce*.

Naštěstí existuje workaround v podobě [PyInstaller][pyinstaller]. Do vývojářského
počítače s Windows se nainstaluje Python, všechny potřebné balíčky a 
`pyinstaller` z Pythonového programu udělá spustitelný .EXE soubor. 
Ten .EXE soubor je pak možné (většinou) spouštět i na jiném počítači, kde Python není.

Ve skutečnosti je v tom EXE souboru zabalený celý Python včetně závislostí, 
při každém spuštění se to rozbalí do `%TEMPDIR%` a po skončení běhu se to zase maže. 
Ale to jsou pro uživatele nepodstatné detaily. 
*Uživatel dostane jeden .EXE soubor, který prostě spustí.*

**Návod na použití** je na webu [pyinstalleru][pyinstaller].

Odzkoušeno na Windows 7, Python 2.7, PyInstaller 2.1.

V případě potřeby je možné celý proces postavení automatizovat 
pomocí Jenkinsu či jiného nástroje.

[pyinstaller]: https://github.com/pyinstaller/pyinstaller/wiki
[matata]: http://www.matata.cz/