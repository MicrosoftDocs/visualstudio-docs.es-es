---
title: Instalación de una aplicación de Shell aislado | Microsoft Docs
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
ms.openlocfilehash: 4d9a7b39dc322ab92458dbd6c7304f672468db17
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851709"
---
# <a name="installing-an-isolated-shell-application"></a>Instalación de una aplicación de Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para instalar una aplicación de Shell debe realizar los pasos siguientes.  
  
- Prepare la solución.  
  
- Cree un paquete de Windows Installer (MSI) para la aplicación.  
  
- Cree un programa previo de instalación.  
  
  Todo el código de ejemplo de este documento procede del [ejemplo de implementación de Shell](https://code.msdn.microsoft.com/Sample-setup-program-for-81ca73f7), que puede descargar de la galería de código en el sitio web de MSDN. En el ejemplo se muestran los resultados de realizar cada uno de estos pasos.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar los procedimientos descritos en este tema, se deben instalar las siguientes herramientas en el equipo.  
  
- El SDK de Visual Studio  
  
- La versión del [conjunto de herramientas de Windows Installer XML](http://wix.sourceforge.net/) 3,6  
  
  El ejemplo también requiere el SDK de visualización y modelado de Microsoft, que no requieren todos los shells.  
  
## <a name="preparing-your-solution"></a>Preparación de la solución  
 De forma predeterminada, las plantillas de Shell se compilan en paquetes VSIX, pero este comportamiento está pensado principalmente para fines de depuración. Al implementar una aplicación de Shell, debe usar paquetes MSI para permitir el acceso al registro y para los reinicios durante la instalación. Para preparar la aplicación para la implementación de MSI, realice los pasos siguientes.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Para preparar una aplicación de Shell para la implementación de MSI  
  
1. Edite cada archivo. vsixmanifest de la solución.  
  
     En el elemento `Identifier`, agregue un elemento `InstalledByMSI` y un elemento `SystemComponent` y, a continuación, establezca sus valores en `true`.  
  
     Estos elementos impiden que el instalador de VSIX intente instalar los componentes y que el usuario los desinstale mediante el cuadro de diálogo **extensiones y actualizaciones** .  
  
2. En cada proyecto que contenga un manifiesto VSIX, edite las tareas de compilación para generar el contenido en la ubicación desde la que se instalará el archivo MSI. Incluya el manifiesto VSIX en la salida de la compilación, pero no cree un archivo. vsix.  
  
## <a name="creating-an-msi-for-your-shell"></a>Creación de un archivo MSI para el shell  
 Para compilar el paquete MSI, se recomienda usar el [conjunto de herramientas de Windows Installer XML](http://wix.sourceforge.net/) porque proporciona mayor flexibilidad que un proyecto de instalación estándar.  
  
 En el archivo product. WXS, establezca los bloques de detección y el diseño de los componentes de Shell.  
  
 A continuación, cree las entradas del registro, tanto en el archivo. reg de la solución como en ApplicationRegistry. WXS.  
  
### <a name="detection-blocks"></a>Bloques de detección  
 Un bloque de detección consta de un elemento `Property` que especifica un requisito previo para detectar y un elemento `Condition` que especifica un mensaje que se va a devolver si el requisito previo no está presente en el equipo. Por ejemplo, la aplicación de Shell requerirá el Microsoft Visual Studio redistribuible de Shell y el bloque de detección será similar al marcado siguiente.  
  
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
 Debe agregar elementos para identificar la estructura de directorios de destino y los componentes que se van a instalar.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Para establecer el diseño de los componentes de Shell  
  
1. Cree una jerarquía de elementos `Directory` para representar todos los directorios que se van a crear en el sistema de archivos en el equipo de destino, como se muestra en el ejemplo siguiente.  
  
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
  
     Se hace referencia a estos directorios mediante `Id` cuando se especifican los archivos que se deben instalar.  
  
2. Identifique los componentes que requiere el Shell y la aplicación de Shell, como se muestra en el ejemplo siguiente.  
  
    > [!NOTE]
    > Algunos elementos pueden hacer referencia a las definiciones de otros archivos. WXS.  
  
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
  
    1. El elemento `ComponentRef` hace referencia a otro archivo. WXS que identifica los archivos que requiere el componente actual. Por ejemplo, GeneralProfile tiene la siguiente definición en HelpAbout. WXS.  
  
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
  
         El elemento `DirectoryRef` especifica dónde van estos archivos en el equipo del usuario. El elemento `Directory` especifica que se instalará en un subdirectorio, y cada elemento `File` representa un archivo compilado o que existe como parte de la solución e identifica dónde se puede encontrar el archivo cuando se crea el archivo MSI.  
  
    2. El elemento `ComponentGroupRef` hace referencia a un grupo de otros componentes (o componentes y grupos de componentes). Por ejemplo, `ComponentGroupRef` en ApplicationGroup se define como sigue en Application. WXS.  
  
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
    > Las dependencias necesarias para las aplicaciones de Shell (aisladas) son: DebuggerProxy, MasterPkgDef, Resources (especialmente el archivo. winprf), Application y PkgDefs.  
  
### <a name="registry-entries"></a>Entradas del Registro  
 La plantilla de proyecto Shell (aislado) incluye un archivo *projectname*. reg para las claves del registro que se van a combinar durante la instalación. Estas entradas del registro deben formar parte de la MSI para fines de instalación y limpieza. También debe crear bloques de registro coincidentes en ApplicationRegistry. WXS.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Para integrar entradas del registro en el MSI  
  
1. En la carpeta de **Personalización de Shell** , Abra *projectname*. reg.  
  
2. Reemplace todas las instancias del $RootFolder $ token por la ruta de acceso del directorio de instalación de destino.  
  
3. Agregue las demás entradas del registro que requiera la aplicación.  
  
4. Abra ApplicationRegistry. WXS.  
  
5. Para cada entrada del registro en *projectname*. reg, agregue un bloque del registro correspondiente, como se muestra en los ejemplos siguientes.  
  
    |*NombreDeProyecto*. reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @ = "Objeto DTE de Fotostudio"|\<RegistryKey Id='DteClsidRegKey' Root='HKCR' Key='$(var.DteClsidRegKey)' Action='createAndRemoveOnUninstall'><br /><br /> \<ID. de tipo = ' cadena ' name = ' @ ' valor = ' $ (var. ShortProductName) objeto DTE '/><br /><br /> \</RegistryKey>|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}\LocalServer32]<br /><br /> @ = "$RootFolder $ \PhotoStudio.exe"|\<RegistryKey Id='DteLocSrv32RegKey' Root='HKCR' Key='$(var.DteClsidRegKey)\LocalServer32' Action='createAndRemoveOnUninstall'><br /><br /> \<RegistryValue Type='string' Name='@' Value='[INSTALLDIR]$(var.ShortProductName).exe' /><br /><br /> \</RegistryKey>|  
  
     En este ejemplo, var. DteClsidRegKey se resuelve en la clave del registro de la fila superior. Var. ShortProductName se resuelve como `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Crear un programa previo de instalación  
 El MSI completado solo se instalará si se instalan primero todos los requisitos previos. Para facilitar la experiencia del usuario final, cree un programa de instalación que recopile e instale todos los requisitos previos antes de instalar la aplicación. Para asegurarse de que la instalación se realiza correctamente, realice estas acciones:  
  
- Aplique la instalación por parte del administrador.  
  
- Detectar si está instalado Visual Studio Shell (aislado).  
  
- Ejecute uno o ambos instaladores de Shell en orden.  
  
- Controlar las solicitudes de reinicio.  
  
- Ejecute el archivo MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Forzar la instalación por parte del administrador  
 Este procedimiento es necesario para permitir que el programa de instalación tenga acceso a los directorios necesarios, como \Archivos de programa\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Para exigir la instalación por parte del administrador  
  
1. Abra el menú contextual del proyecto de instalación y, a continuación, elija **propiedades**.  
  
2. En **propiedades de configuración/vinculador/archivo de manifiesto**, establezca el **nivel de ejecución de UAC** en **requireAdministrator**.  
  
     Esta propiedad coloca el atributo que requiere que el programa se ejecute como administrador en el archivo de manifiesto incrustado.  
  
### <a name="detecting-shell-installations"></a>Detectar instalaciones de Shell  
 Para determinar si se debe instalar Visual Studio Shell (aislado), determine primero si ya está instalado mediante la comprobación del valor del registro de HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
> Estos valores también los lee el bloque de detección de Shell en product. WXS.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder especifica la ubicación en la que se instaló Visual Studio Shell y puede comprobar si hay archivos allí.  
  
 Para obtener un ejemplo de cómo detectar una instalación de Shell, consulte la función `GetProductDirFromReg` de Utilities. cpp en el ejemplo de implementación de Shell.  
  
 Si uno de los shells de Visual Studio que requiere el paquete no está instalado en el equipo, debe agregarlos a la lista de componentes que se van a instalar. Para obtener un ejemplo, consulte la función `ComponentsPage::OnInitDialog` de ComponentsPage. cpp en el ejemplo de implementación de Shell.  
  
### <a name="running-the-shell-installers"></a>Ejecución de los instaladores de Shell  
 Para ejecutar los instaladores de Shell, llame a los redistribuibles de Visual Studio Shell mediante los argumentos de línea de comandos correctos. Como mínimo, debe usar los argumentos de la línea de comandos **/norestart/q** y ver el código de retorno para determinar lo que se debe hacer a continuación. En el ejemplo siguiente se ejecuta el paquete redistribuible de Shell (aislado).  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Ejecución de los instaladores de paquetes de idioma de Shell  
 Si en su lugar encuentra que el shell o los shells se han instalado y solo necesita un paquete de idioma, puede instalar los paquetes de idioma como se muestra en el ejemplo siguiente.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Descifrar los valores devueltos  
 En algunos sistemas operativos, la instalación de Visual Studio Shell (aislado) requerirá un reinicio. Esta condición se puede determinar mediante el código de retorno de la llamada a `ExecCmd`.  
  
|Valor devuelto|Descripción|  
|------------------|-----------------|  
|ERROR_SUCCESS|Instalación completada. Ahora puede instalar la aplicación.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Instalación completada. Puede instalar la aplicación después de reiniciar el equipo.|  
|3015|La instalación está en curso. Es necesario reiniciar el equipo para continuar con la instalación.|  
  
### <a name="handling-restarts"></a>Administrar reinicios  
 Cuando se ejecutó el instalador de Shell mediante el argumento **/norestart** , se especificó que no se reiniciara el equipo o se pediría que se reiniciara el equipo. Sin embargo, es posible que se requiera un reinicio, y debe asegurarse de que el instalador continúa después de reiniciar el equipo.  
  
 Para controlar los reinicios correctamente, asegúrese de que solo se ha configurado un programa de instalación para que se reanude y que el proceso de reanudación se controlará correctamente.  
  
 Si se devuelve ERROR_SUCCESS_REBOOT_REQUIRED o 3015, el código debe reiniciar el equipo antes de continuar con la instalación.  
  
 Para controlar los reinicios, realice estas acciones:  
  
- Establezca el registro para reanudar la instalación cuando se inicie Windows.  
  
- Realice un reinicio doble del programa previo.  
  
- Elimine la clave ResumeData del instalador de Shell.  
  
- Reinicie Windows.  
  
- Restablezca la ruta de acceso de inicio del archivo MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Configuración del registro para reanudar la instalación cuando se inicia Windows  
 La clave del registro HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ se ejecuta al iniciar el sistema con permisos administrativos y, a continuación, se borra. HKEY_CURRENT_USER contiene una clave similar, pero se ejecuta como un usuario normal y no es adecuado para las instalaciones de. Puede reanudar la instalación colocando un valor de cadena en la clave RunOnce que llama al instalador. Sin embargo, se recomienda llamar al instalador mediante un parámetro **/restart** o similar para notificar a la aplicación que se está reanudando en lugar de iniciarse. También puede incluir parámetros para indicar dónde se encuentra en el proceso de instalación, lo que es especialmente útil en las instalaciones que pueden requerir varios reinicios.  
  
 En el ejemplo siguiente se muestra un valor de clave del registro RunOnce para reanudar una instalación.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Instalación del inicio doble de arranque  
 Si el programa de instalación se usa directamente desde RunOnce, el escritorio no podrá cargarse por completo. Para que la interfaz de usuario completa esté disponible, debe crear otra ejecución del programa de instalación y finalizar la instancia RunOnce.  
  
 Debe volver a ejecutar el programa de instalación para que obtenga los permisos correctos y debe proporcionar información suficiente para saber dónde se detuvo antes del reinicio, como se muestra en el ejemplo siguiente.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Eliminando la clave ResumeData del instalador de Shell  
 El instalador de Shell establece la clave del registro HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData con datos para reanudar la instalación después del reinicio. Dado que la aplicación, no el instalador de Shell, se está reanudando, elimine la clave del registro, como se muestra en el ejemplo siguiente.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Reiniciar Windows  
 Después de establecer las claves del registro necesarias, puede reiniciar Windows. En el ejemplo siguiente se invocan los comandos de reinicio para los distintos sistemas operativos Windows.  
  
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
  
### <a name="resetting-the-start-path-of-msi"></a>Restablecer la ruta de acceso de inicio de MSI  
 Antes del reinicio, el directorio actual es la ubicación del programa de instalación pero, después del reinicio, la ubicación se convierte en el directorio system32. El programa de instalación debe restablecer el directorio actual antes de cada llamada de MSI, como se muestra en el ejemplo siguiente.  
  
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
  
### <a name="running-the-application-msi"></a>Ejecución de la aplicación MSI  
 Después de que el instalador de Visual Studio Shell devuelva ERROR_SUCCESS, puede ejecutar el archivo MSI para la aplicación. Como el programa de instalación proporciona la interfaz de usuario, inicie el MSI en modo silencioso ( **/q**) y con el registro ( **/l**), como se muestra en el ejemplo siguiente.  
  
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
 [Tutorial: creación una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
