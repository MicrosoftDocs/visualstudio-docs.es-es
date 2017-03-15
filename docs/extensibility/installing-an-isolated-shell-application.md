---
title: "Instalaci&#243;n de una aplicaci&#243;n de Shell aislado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Implementar aplicaciones basadas en el shell de shell [Visual Studio]"
  - "Shell de Visual Studio, implementar aplicaciones basadas en shell"
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 40
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 40
---
# Instalaci&#243;n de una aplicaci&#243;n de Shell aislado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Debe realizar los pasos siguientes para instalar una aplicación de Shell.  
  
-   Prepare su solución.  
  
-   Crear un paquete de Windows Installer \(MSI\) para la aplicación.  
  
-   Crear a un programa previo de instalación.  
  
 Todo el código de ejemplo en este documento proviene de la [ejemplo de implementación de Shell](http://go.microsoft.com/fwlink/?LinkId=262245), que puede descargar desde la Galería de código en el sitio Web MSDN. El ejemplo muestra los resultados de la realización de cada uno de estos pasos.  
  
## Requisitos previos  
 Para llevar a cabo los procedimientos de este tema se describen las siguientes herramientas deben instalarse en el equipo.  
  
-   El SDK de Visual Studio  
  
-   El [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) versión 3.6  
  
 El ejemplo también requiere el Visualization de Microsoft y SDK de modelado, que requieren que no todos los shells.  
  
## Preparación de la solución  
 De forma predeterminada, crear plantillas de Shell en paquetes VSIX, pero este comportamiento está diseñado principalmente para fines de depuración. Al implementar una aplicación de Shell, debe utilizar paquetes MSI para permitir para acceder al registro y los reinicios durante la instalación. Para preparar la aplicación para la implementación de MSI, realice los pasos siguientes.  
  
#### Para preparar una aplicación de Shell para la implementación de MSI  
  
1.  Modificar cada archivo .vsixmanifest en la solución.  
  
     En el `Identifier` elemento, agregue un `InstalledByMSI` elemento y un `SystemComponent` elemento y, a continuación, establezca los valores `true`.  
  
     Estos elementos de impedir que el instalador VSIX intentando instalar los componentes y el usuario de desinstalar usando el **extensiones y actualizaciones** cuadro de diálogo.  
  
2.  Para cada proyecto que contiene un manifiesto VSIX, edite las tareas de compilación para generar el contenido a la ubicación desde la que se instalará el MSI. Incluir el manifiesto de VSIX en la salida de compilación, pero no se crea un archivo .vsix.  
  
## Crear un archivo MSI del shell  
 Para crear el paquete MSI, se recomienda que utilice la [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) porque proporciona mayor flexibilidad que un proyecto de instalación estándar.  
  
 En el archivo Product.wxs, establecer bloques de detección y el diseño de los componentes de Shell.  
  
 A continuación, cree las entradas del registro tanto en el archivo .reg para su solución en ApplicationRegistry.wxs.  
  
### Bloques de detección  
 Un bloque de detección se compone de un `Property` elemento que especifica un requisito previo para detectar y un `Condition` elemento que especifica un mensaje que se devuelve si el requisito previo no está presente en el equipo. Por ejemplo, la aplicación de Shell requiere Microsoft Visual Studio Shell redistributable, y el bloque de detección se parecerá a la revisión siguiente.  
  
```xml  
<Property Id="ISOSHELLSFX"> <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Property Id="INTSHELLSFX"> <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again."> <![CDATA[Installed OR ISOSHELLSFX]]> </Condition> <Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again."> <![CDATA[Installed OR INTSHELLSFX]]> </Condition>  
  
```  
  
### Diseño de componentes de Shell  
 Debe agregar elementos para identificar la estructura de directorios de destino y los componentes que desea instalar.  
  
##### Para establecer el diseño de componentes de Shell  
  
1.  Crear una jerarquía de `Directory` elementos para representar todos los directorios para crear en el sistema de archivos en el equipo de destino, como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir"> <Directory Id="ProgramFilesFolder"> <Directory Id="CompanyDirectory" Name="$(var.CompanyName)"> <Directory Id="INSTALLDIR" Name="$(var.FullProductName)"> <Directory Id="ExtensionsFolder" Name="Extensions" /> <Directory Id="Folder1033" Name="1033" /> </Directory> </Directory> </Directory> <Directory Id="ProgramMenuFolder"> <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/> </Directory> </Directory>  
    ```  
  
     Estos directorios se denominan mediante `Id` cuando se especifican los archivos que se deben instalar.  
  
2.  Identificar los componentes que requieren el Shell y la aplicación de Shell, como se muestra en el ejemplo siguiente.  
  
    > [!NOTE]
    >  Algunos elementos pueden hacer referencia a las definiciones de otros archivos wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1"> <ComponentGroupRef Id="ApplicationGroup" /> <ComponentGroupRef Id="HelpAboutPackage" /> <ComponentRef Id="GeneralProfile" /> <ComponentGroupRef Id="EditorAdornment"/> <ComponentGroupRef Id="SlideShowDesignerGroup"/> <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. --> <ComponentGroupRef Id="Product.Generated" /> </Feature>  
    ```  
  
    1.  El `ComponentRef` elemento hace referencia a otro archivo wxs que identifica los archivos que requiere el componente actual. Por ejemplo, GeneralProfile tiene la siguiente definición en HelpAbout.wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles"> <DirectoryRef Id="INSTALLDIR"> <Directory Id="ProfilesFolder" Name="Profiles"> <Component Id='GeneralProfile' Guid='*'> <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' /> </Component> </Directory> </DirectoryRef> </Fragment>  
        ```  
  
         El `DirectoryRef` elemento especifica adónde estos archivos en el equipo del usuario. El `Directory` elemento especifica que se va a instalar en un subdirectorio y cada `File` elemento representa un archivo que se compila o que existe como parte de la solución e identifica dónde puede encontrarse ese archivo cuando se crea el archivo MSI.  
  
    2.  El `ComponentGroupRef` elemento hace referencia a un grupo de otros componentes \(o los componentes y los grupos de componentes\). Por ejemplo, `ComponentGroupRef` en ApplicationGroup se define como sigue en Application.wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup"> <ComponentGroupRef Id="DebuggerProxy" /> <ComponentRef Id="MasterPkgDef" /> <ComponentRef Id="SplashResource" /> <ComponentRef Id="IconResource" /> <ComponentRef Id="WinPrfResource" /> <ComponentRef Id="AppExe" /> <ComponentRef Id="AppConfig" /> <ComponentRef Id="AppPkgDef" /> <ComponentRef Id="AppPkgDefUndef" /> <ComponentRef Id="$(var.ShortProductName)UI1033" /> <ComponentRef Id="ApplicationShortcut"/> <ComponentRef Id="ApplicationRegistry"/> </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Necesarios son las dependencias de aplicaciones de Shell \(aislado\): DebuggerProxy, MasterPkgDef, recursos \(especialmente el archivo .winprf\), aplicación y PkgDefs.  
  
### Entradas del Registro  
 La plantilla de proyecto de Shell \(aislado\) incluye un *ProjectName*archivo .reg para claves del registro para combinar en la instalación. Estas entradas del registro deben formar parte de MSI para la instalación y con fines de limpieza. También debe crear bloques de registro correspondiente en ApplicationRegistry.wxs.  
  
##### Para integrar las entradas del registro en el archivo MSI  
  
1.  En el **Shell personalización** carpeta, abra *ProjectName*. reg.  
  
2.  Reemplace todas las instancias del token de $ $RootFolder por la ruta de acceso del directorio de instalación de destino.  
  
3.  Agregue las entradas de registro que requiere su aplicación.  
  
4.  Abra ApplicationRegistry.wxs.  
  
5.  Para cada entrada del registro de *ProjectName*. reg, agregar un bloque de registro correspondiente, como muestran los ejemplos siguientes.  
  
    |*ProjectName*. reg|ApplicationRegisty.wxs|  
    |------------------------|----------------------------|  
    |\[HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6}\]<br /><br /> @\= "Objeto DTE PhotoStudio"|\< Id. de RegistryKey \= raíz 'DteClsidRegKey' \= 'HKCR' Key \=' $\(var.\) DteClsidRegKey\)' acción \= 'createAndRemoveOnUninstall' \><br /><br /> \< RegistryValue tipo \= 'cadena' nombre \=' @' valor \=' $\(var.\) Objeto ShortProductName\) DTE' \/ \><br /><br /> \< \/ RegistryKey \>|  
    |\[\\LocalServer32 HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6}\]<br /><br /> @\= "$RootFolder$\\PhotoStudio.exe"|\< Id. de RegistryKey \= raíz 'DteLocSrv32RegKey' \= 'HKCR' Key \=' $\(var.\) DteClsidRegKey\) \\LocalServer32' acción \= 'createAndRemoveOnUninstall' \><br /><br /> \< RegistryValue tipo \= 'cadena' nombre \=' @' valor \='\[INSTALLDIR\] $\(var.\) .Exe ShortProductName\)' \/ \><br /><br /> \< \/ RegistryKey \>|  
  
     En este ejemplo, Var.DteClsidRegKey se resuelve como la clave del registro en la fila superior. Var.ShortProductName se resuelve como `PhotoStudio`.  
  
## Crear un programa de instalación arranque  
 Se instalará el MSI completado solo si todos los requisitos previos se instalan en primer lugar. Para facilitar la experiencia del usuario final, crear un programa de instalación que recopila e instala todos los requisitos previos antes de instalar la aplicación. Para garantizar una instalación correcta, realice estas acciones:  
  
-   Exigir la instalación de administrador.  
  
-   Detectar si está instalado Visual Studio Shell \(aislado\).  
  
-   Uno o ambos instaladores de Shell se ejecutan en orden.  
  
-   Administrar solicitudes de reinicio.  
  
-   Ejecute el MSI.  
  
### Exigir la instalación de administrador  
 Este procedimiento es necesario para habilitar el programa de instalación tener acceso a los directorios necesarios como \\Program Files\\.  
  
##### Para exigir la instalación de administrador  
  
1.  Abra el menú contextual del proyecto de instalación y, a continuación, elija **propiedades**.  
  
2.  Bajo **archivo de configuración de vinculador\/propiedades\/manifiesto**, establezca **nivel de ejecución de UAC** a **requireAdministrator**.  
  
     Esta propiedad hace que el atributo que requiere el programa para ejecutarse como administrador en el archivo de manifiesto incrustado.  
  
### Detectar instalaciones de Shell  
 Para determinar si se debe instalar Visual Studio Shell \(aislado\), determinar primero si ya está instalado, compruebe el valor del registro de HKLM\\Software\\Microsoft\\DevDiv\\vs\\Servicing\\ShellVersion\\isoshell\\LCID\\Install.  
  
> [!NOTE]
>  Estos valores también se leen el bloque de detección de Shell en Product.wxs.  
  
 HKLM\\Software\\Microsoft\\AppEnv\\14.0\\ShellFolder Especifica la ubicación donde se instaló el Shell de Visual Studio y puede buscar los archivos.  
  
 Para obtener un ejemplo de cómo detectar una instalación de Shell, consulte el `GetProductDirFromReg` función de Utilities.cpp en el ejemplo de implementación de Shell.  
  
 Si uno o ambos de los Shells de Visual Studio que necesita el paquete no está instalado en el equipo, debe agregarlos a la lista de componentes que desea instalar. Para obtener un ejemplo, consulte el `ComponentsPage::OnInitDialog` función de ComponentsPage.cpp en el ejemplo de implementación de Shell.  
  
### Ejecuta a los instaladores de Shell  
 Para ejecutar a los instaladores de Shell, llamar a los archivos redistribuibles de Visual Studio Shell utilizando los argumentos de línea de comandos correctos. Como mínimo, debe usar los argumentos de línea de comandos **\/norestart \/q** y observe el código de retorno determinar qué se debe hacer a continuación. En el ejemplo siguiente se ejecuta el paquete redistribuible Shell \(aislado\).  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### Ejecuta a los instaladores de paquete de idioma de Shell  
 Si encuentra que está instalados el shell o shells y sólo necesita un paquete de idioma de en su lugar, puede instalar los paquetes de idioma como se muestra en el ejemplo siguiente.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### Descifrado de valores devueltos  
 En algunos sistemas operativos, la instalación de Visual Studio Shell \(aislado\) requerirá un reinicio. Esta condición se puede determinar mediante el código de retorno de la llamada a `ExecCmd`.  
  
|Valor devuelto|Descripción|  
|--------------------|-----------------|  
|ERROR\_SUCCESS|Instalación finalizada. Ahora puede instalar la aplicación.|  
|ERROR\_SUCCESS\_REBOOT\_REQUIRED|Instalación finalizada. Puede instalar la aplicación una vez reiniciado el equipo.|  
|3015|Instalación está en curso. Se requiere un reinicio del equipo para continuar la instalación.|  
  
### Control de reinicio  
 Cuando se ejecutaba el instalador del Shell mediante el **\/norestart** argumento, especifica que no reinicie el equipo o pedir que se reinicie el equipo. Sin embargo, puede ser necesario un reinicio, y debe asegurarse de que el instalador continúa después de reiniciar el equipo.  
  
 Para controlar correctamente los reinicios, asegúrese de que sólo un programa de instalación está establecido en reanudar y que el proceso de reanudación se controlará correctamente.  
  
 Si se devuelve ERROR\_SUCCESS\_REBOOT\_REQUIRED o 3015, el código debe reiniciar el equipo antes de seguir con la instalación.  
  
 Para controlar los reinicios, realice estas acciones:  
  
-   Configurar el registro para reanudar la instalación cuando se inicia Windows.  
  
-   Realizar un reinicio del arranque doble.  
  
-   Elimine la clave de ResumeData del instalador de Shell.  
  
-   Reinicie Windows.  
  
-   Restablecer la ruta de acceso de inicio de MSI.  
  
### Configurar el registro para reanudar la instalación cuando se inicia Windows  
 El HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\RunOnce\\ clave del registro se ejecuta al iniciar el sistema con permisos administrativos y, a continuación, se borra.HKEY\_CURRENT\_USER contiene una clave similar, pero se ejecuta como un usuario normal y no es adecuada para las instalaciones. Para reanudar la instalación colocando un valor de cadena en la clave de RunOnce que llama el programa de instalación. Sin embargo, se recomienda que llame el programa de instalación mediante un **\/restart** o parámetro similar para notificar a la aplicación que está reanudando en lugar de iniciarse. También puede incluir parámetros para indicar dónde se encuentre en el proceso de instalación, que es especialmente útil en instalaciones que pueden requerir varios reinicios.  
  
 En el ejemplo siguiente se muestra un valor de clave del registro de RunOnce para reanudar la instalación.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### Reinicio dobles de programa previo de instalación  
 Si se utiliza el programa de instalación directamente desde RunOnce, el escritorio no podrá cargar completamente. Para disponer de la interfaz de usuario completo, debe crear otra ejecución del programa de instalación y finalizar la instancia de RunOnce.  
  
 Debe volver a ejecutar el programa de instalación para que obtiene los permisos correctos y debe proporcionar información suficiente para saber dónde se detuvo antes del reinicio, como se muestra en el ejemplo siguiente.  
  
```  
if (_cmdLineInfo.IsRestart()) { TCHAR path[MAX_PATH]={0}; GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR)); ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL ); }  
  
```  
  
### Al eliminar la clave de ResumeData del instalador de Shell  
 El instalador de Shell se establece el HKLM\\Software\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData la clave del registro con datos que se va a reanudar la instalación después del reinicio. Ya se está reanudando la aplicación, no el instalador del Shell, eliminar esa clave del registro, como se muestra en el ejemplo siguiente.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData")); RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### Reinicio de Windows  
 Después de establecer las claves del registro necesarias, puede reiniciar Windows. En el ejemplo siguiente se invoca los comandos de reinicio para distintos sistemas operativos Windows.  
  
```  
OSVERSIONINFO ov; HANDLE htoken ; //Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown. if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken)) { LUID luid ; LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ; TOKEN_PRIVILEGES    privs ; privs.Privileges[0].Luid = luid ; privs.PrivilegeCount = 1 ; privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ; AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ; } //Use InitiateSystemShutdownEx to avoid unexpected restart message box try { if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) )) { bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG); } else { #pragma prefast(suppress:380,"ignore warning about legacy api") bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE); } } catch(...) { //advapi32.dll call not available! Will not restart! }  
  
```  
  
### Restablecimiento de la ruta de acceso de inicio de MSI  
 Antes de reiniciar, el directorio actual es la ubicación del programa de instalación, pero después del reinicio, la ubicación, se convierte en el directorio system32. El programa de instalación debe restablecer el directorio actual antes de cada llamada MSI, como se muestra en el ejemplo siguiente.  
  
```  
CString GetSetupPath() { TCHAR file[MAX_PATH]; GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR)); CString path(file); int fpos = path.ReverseFind('\\'); if (fpos != -1) { path = path.Left(fpos + 1); } return path; }  
  
```  
  
### Ejecutar la aplicación MSI  
 Después de que el instalador de Visual Studio Shell devuelve ERROR\_SUCCESS, puede ejecutar el MSI de la aplicación. Dado que el programa de instalación proporciona la interfaz de usuario, inicie el MSI en modo silencioso \(**\/q**\) y con el registro \(**\/L**\), como se muestra en el ejemplo siguiente.  
  
```cpp#  
TCHAR temp[MAX_PATH]; GetTempPath(MAX_PATH, temp); CString boutiqueInstallCmd, msi, log; CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress")); CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi")); log.Format(_T("\"%s%s.log\""), temp, name); msi.Format(_T("\"%s%s\""), GetSetupPath(), name); boutiqueInstallCmd.Format(cmdLine, msi, log); //TODO: You can use MSI API to gather and present install progress feedback from your MSI. dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## Vea también  
 [Tutorial: Crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)