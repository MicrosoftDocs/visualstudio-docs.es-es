---
title: Instalar una aplicación de Shell aislado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 55c4ebc96d93d9b068c29d24727d40975518b1ef
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60062833"
---
# <a name="installing-an-isolated-shell-application"></a>Instalar una aplicación de Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debe realizar los pasos siguientes para instalar una aplicación de Shell.  
  
- Prepare su solución.  
  
- Crear un paquete de Windows Installer (MSI) para la aplicación.  
  
- Crear a un programa previo de instalación.  
  
  Todo el código de ejemplo en este documento proviene de la [ejemplo de implementación de Shell](http://go.microsoft.com/fwlink/?LinkId=262245), que puede descargar desde la Galería de código en el sitio Web MSDN. El ejemplo muestra los resultados de llevar a cabo cada uno de estos pasos.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para llevar a cabo los procedimientos descritos en este tema, las siguientes herramientas deben instalarse en el equipo.  
  
- El SDK de Visual Studio  
  
- El [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) versión 3.6  
  
  El ejemplo también requiere el Microsoft Visualization y el SDK de modelado, que no todos los shells requieren.  
  
## <a name="preparing-your-solution"></a>Preparación de la solución  
 De forma predeterminada, las plantillas de Shell se basan en paquetes VSIX, pero este comportamiento está diseñado principalmente para fines de depuración. Al implementar una aplicación de Shell, debe usar los paquetes MSI para permitir para acceder al registro y los reinicios durante la instalación. Para preparar la aplicación para la implementación de MSI, realice los pasos siguientes.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Para preparar una aplicación de Shell para la implementación de MSI  
  
1. Edite cada archivo .vsixmanifest en la solución.  
  
     En el `Identifier` elemento, agregue un `InstalledByMSI` elemento y un `SystemComponent` elemento y, a continuación, establezca sus valores en `true`.  
  
     Estos elementos impiden que el instalador de VSIX se intentar instalar los componentes y el usuario desde su desinstalación mediante el uso de la **extensiones y actualizaciones** cuadro de diálogo.  
  
2. Para cada proyecto que contiene un manifiesto VSIX, edite las tareas de compilación para generar el contenido a la ubicación desde la que se instalará el MSI. Incluir el manifiesto de VSIX en la salida de compilación, pero no cree un archivo. vsix.  
  
## <a name="creating-an-msi-for-your-shell"></a>Creación de un archivo MSI de Shell  
 Para crear el paquete MSI, se recomienda que use el [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) porque ofrece mayor flexibilidad que un proyecto de instalación estándar.  
  
 En el archivo Product.wxs, establezca los bloques de detección y el diseño de componentes de Shell.  
  
 A continuación, crear entradas del registro, en el archivo .reg para su solución y en ApplicationRegistry.wxs.  
  
### <a name="detection-blocks"></a>Bloques de detección  
 Un bloque de detección se compone de un `Property` elemento que especifica un requisito previo para detectar y un `Condition` elemento que especifica un mensaje que se devuelve si el requisito previo no está presente en el equipo. Por ejemplo, la aplicación de Shell necesitará Microsoft Visual Studio Shell redistributable, y el bloque de detección se parecerá a la marcación siguiente.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Diseño de componentes de Shell  
 Debe agregar los elementos para identificar la estructura de directorios de destino y los componentes que desea instalar.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Para establecer el diseño de componentes de Shell  
  
1. Crear una jerarquía de `Directory` elementos para representar todos los directorios para crear en el sistema de archivos en el equipo de destino, como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     Estos directorios se denominan mediante `Id` cuando se especifican los archivos que se deben instalar.  
  
2. Identificar los componentes que requieren el Shell y la aplicación de Shell, como se muestra en el ejemplo siguiente.  
  
    > [!NOTE]
    >  Algunos elementos pueden hacer referencia a las definiciones de otros archivos wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1. El `ComponentRef` elemento hace referencia a otro archivo wxs que identifica los archivos que requiere el componente actual. Por ejemplo, GeneralProfile tiene la siguiente definición en HelpAbout.wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         El `DirectoryRef` elemento especifica dónde estos archivos en el equipo del usuario. El `Directory` elemento especifica que se va a instalar en un subdirectorio y cada uno de ellos `File` elemento representa un archivo que se compila o que existe como parte de la solución e identifica dónde puede encontrarse ese archivo cuando se crea el archivo MSI.  
  
    2. El `ComponentGroupRef` elemento hace referencia a un grupo de otros componentes (o los componentes y los grupos de componentes). Por ejemplo, `ComponentGroupRef` en ApplicationGroup se define como sigue en Application.wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Son dependencias necesarias para las aplicaciones de Shell (aislado): DebuggerProxy, MasterPkgDef, recursos (especialmente el archivo .winprf), aplicación y PkgDefs.  
  
### <a name="registry-entries"></a>Entradas del Registro  
 La plantilla de proyecto de Shell (aislado) incluye un *ProjectName*archivo .reg para las claves del registro fusionar mediante combinación en la instalación. Estas entradas del registro deben formar parte de MSI para la instalación y con fines de limpieza. También debe crear bloques de registro coincidente en ApplicationRegistry.wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Para integrar las entradas del registro en el archivo MSI  
  
1. En el **Shell personalización** carpeta abierta *ProjectName*. reg.  
  
2. Reemplace todas las instancias del token $ $RootFolder por la ruta de acceso del directorio de instalación de destino.  
  
3. Agregue las entradas de registro que requiera la aplicación.  
  
4. Abra ApplicationRegistry.wxs.  
  
5. Para cada entrada del registro en *ProjectName*. reg, agregue un bloque de registro correspondiente, como los siguientes ejemplos se muestran.  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "Objeto DTE PhotoStudio"|\<RegistryKey Id='DteClsidRegKey' Root='HKCR' Key='$(var.DteClsidRegKey)' Action='createAndRemoveOnUninstall'><br /><br /> \<RegistryValue Type='string' Name='@' Value='$(var.ShortProductName) DTE Object' /><br /><br /> \</RegistryKey>|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}\LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey Id='DteLocSrv32RegKey' Root='HKCR' Key='$(var.DteClsidRegKey)\LocalServer32' Action='createAndRemoveOnUninstall'><br /><br /> \<RegistryValue Type='string' Name='@' Value='[INSTALLDIR]$(var.ShortProductName).exe' /><br /><br /> \</RegistryKey>|  
  
     En este ejemplo, Var.DteClsidRegKey se resuelve como la clave del registro en la fila superior. Se resuelve como Var.ShortProductName `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Creación de un programa previo de instalación  
 El MSI completa se instalará solo si todos los requisitos previos se instalan en primer lugar. Para facilitar la experiencia del usuario final, crear un programa de instalación que se recopila e instala todos los requisitos previos antes de instalar la aplicación. Para garantizar una instalación correcta, realice estas acciones:  
  
- Forzar la instalación de administrador.  
  
- Detectar si está instalado Visual Studio Shell (aislado).  
  
- Uno o ambos instaladores de Shell se ejecutan en orden.  
  
- Controlar las solicitudes de reinicio.  
  
- Ejecute el MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Forzar la instalación de administrador  
 Este procedimiento es necesario para habilitar el programa de instalación tener acceso a los directorios necesarios como archivos \Program\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Para forzar la instalación de administrador  
  
1. Abra el menú contextual del proyecto de instalación y, a continuación, elija **propiedades**.  
  
2. En **archivo de configuración de vinculador/propiedades/manifiesto**, establezca **nivel de ejecución de UAC** a **requireAdministrator**.  
  
     Esta propiedad coloca el atributo que requiere el programa para ejecutarse como administrador en el archivo de manifiesto incrustado.  
  
### <a name="detecting-shell-installations"></a>Detectar instalaciones de Shell  
 Para determinar si se debe instalar Visual Studio Shell (aislado), determine primero si ya está instalado comprobando el valor del registro de HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  El bloque de detección de Shell en Product.wxs también leen estos valores.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder especifica la ubicación donde se instaló Visual Studio Shell, y puede comprobar si hay archivos en ella.  
  
 Para obtener un ejemplo de cómo detectar una instalación de Shell, consulte el `GetProductDirFromReg` función de Utilities.cpp en el ejemplo de implementación de Shell.  
  
 Si uno o ambos de los Shells de Visual Studio que necesita el paquete no está instalado en el equipo, debe agregarlos a la lista de componentes que desea instalar. Para obtener un ejemplo, vea el `ComponentsPage::OnInitDialog` función de ComponentsPage.cpp en el ejemplo de implementación de Shell.  
  
### <a name="running-the-shell-installers"></a>Ejecuta a los instaladores de Shell  
 Para ejecutar a los instaladores de Shell, llame a los archivos redistribuibles de Visual Studio Shell mediante el uso de los argumentos de línea de comandos correctos. Como mínimo, debe usar los argumentos de línea de comandos **/q /norestart** y espere a que el código de retorno determinar qué se debe hacer a continuación. En el siguiente ejemplo se ejecuta el Shell (aislado) paquete redistribuible.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Ejecuta a los instaladores de paquete de idioma de Shell  
 Si encuentra que está instalados el shell o shells y solo necesita un paquete de idioma de en su lugar, puede instalar los paquetes de idioma como se muestra en el ejemplo siguiente.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Descifrando los valores devueltos  
 En algunos sistemas operativos, la instalación de Visual Studio Shell (aislado) requerirá un reinicio. Esta condición se puede determinar mediante el código de retorno de la llamada a `ExecCmd`.  
  
|Valor devuelto|Descripción|  
|------------------|-----------------|  
|ERROR_SUCCESS|Instalación completada. Ahora puede instalar la aplicación.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Instalación completada. Puede instalar la aplicación después de reiniciar el equipo.|  
|3015|Instalación está en curso. Es necesario reiniciar el equipo para continuar con la instalación.|  
  
### <a name="handling-restarts"></a>Controlar los reinicios  
 Cuando se ejecutó el instalador del Shell mediante el uso de la **/norestart** argumento, especifica que no reinicie el equipo o pedir que se reinicie el equipo. Sin embargo, es posible que se requiera un reinicio, y debe asegurarse de que el instalador continúa después de reiniciar el equipo.  
  
 Para controlar correctamente los reinicios, asegúrese de que solo un programa de instalación está establecido en reanudar y que se controlarán correctamente el proceso de reanudación.  
  
 Si se devuelve ERROR_SUCCESS_REBOOT_REQUIRED o 3015, el código debe reiniciar el equipo antes de que continúe la instalación.  
  
 Para controlar los reinicios, realice estas acciones:  
  
- Configurar el registro para reanudar la instalación cuando se inicia Windows.  
  
- Realizar un reinicio del arranque doble.  
  
- Eliminar la clave de ResumeData del instalador de Shell.  
  
- Reinicie Windows.  
  
- Restablecimiento de la ruta de acceso de inicio de MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Configuración del registro para reanudar la instalación cuando se inicia Windows  
 La clave del registro HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ ejecuta al iniciar el sistema con permisos administrativos y, a continuación, se borra. HKEY_CURRENT_USER contiene una clave similar, pero se ejecuta como un usuario normal y no es adecuada para las instalaciones. Para reanudar la instalación mediante la colocación de un valor de cadena en la que llama al instalador de la clave de RunOnce. Sin embargo, se recomienda que llame el programa de instalación mediante un **/reiniciará** o parámetro similar para notificar a la aplicación que está reanudando en lugar de iniciarse. También puede incluir parámetros para indicar dónde se encuentre en el proceso de instalación, que es especialmente útil en las instalaciones que pueden requerir varios reinicios.  
  
 El ejemplo siguiente muestra un valor de clave del registro de RunOnce para reanudar una instalación.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Double reinicio del programa previo de instalación  
 Si se usa el programa de instalación directamente desde RunOnce, el escritorio no podrá cargar por completo. Para que la interfaz de usuario completa esté disponible, debe crear otra ejecución del programa de instalación y finalizar la instancia de RunOnce.  
  
 Debe volver a ejecutar el programa de instalación para que obtiene los permisos correctos, y debe proporcionar suficiente información para saber dónde se detuvo antes del reinicio, como se muestra en el ejemplo siguiente.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Eliminando la clave de Shell Installer ResumeData  
 El instalador del Shell establece la clave del registro HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData con datos para reanudar la instalación tras el reinicio. Dado que la aplicación, no el instalador del Shell, se reanuda, elimine esa clave del registro, como se muestra en el ejemplo siguiente.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Reinicio de Windows  
 Después de establecer las claves del registro necesarias, puede reiniciar Windows. El ejemplo siguiente invoca los comandos de reinicio para diferentes sistemas operativos de Windows.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>Restableciendo la ruta de acceso de inicio de MSI  
 Antes de reiniciar, el directorio actual es la ubicación de su programa de instalación pero, después del reinicio, la ubicación, se convierte en el directorio system32. El programa de instalación debe restablecer el directorio actual antes de cada llamada MSI, como se muestra en el ejemplo siguiente.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>Ejecutar la aplicación MSI  
 Después de que el instalador de Visual Studio Shell devuelve ERROR_SUCCESS, puede ejecutar el archivo MSI para la aplicación. Dado que el programa de instalación proporciona la interfaz de usuario, inicie la MSI en modo silencioso (**/q**) y con el registro (**/l**), tal y como se muestra en el ejemplo siguiente.  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Creación de una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
