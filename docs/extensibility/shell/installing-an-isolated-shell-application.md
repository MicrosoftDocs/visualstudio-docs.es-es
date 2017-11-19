---
title: "Instalar una aplicación de Shell aislado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: "40"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afe5ddd5748fe0d8f394a63898370eaf405b3f4e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="installing-an-isolated-shell-application"></a>Instalar una aplicación de Shell aislado
Debe realizar los pasos siguientes para instalar una aplicación de Shell.  
  
-   Prepare su solución.  
  
-   Crear un paquete de Windows Installer (MSI) para la aplicación.  
  
-   Crear a un programa previo de instalación.  
  
 Todo el código de ejemplo en este documento procede de la [ejemplo de implementación de Shell](http://go.microsoft.com/fwlink/?LinkId=262245), que puede descargar desde la Galería de código en el sitio Web de MSDN. El ejemplo muestra el resultado de realizar cada uno de estos pasos.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para llevar a cabo los procedimientos descritos en este tema, las siguientes herramientas deben instalarse en el equipo.  
  
-   El SDK de Visual Studio  
  
-   El [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) versión 3.6  
  
 El ejemplo también requiere el Visualization de Microsoft y el SDK de modelado, que requieren que no todos los shells.  
  
## <a name="preparing-your-solution"></a>Preparación de la solución  
 De forma predeterminada, las plantillas de Shell de compilación a los paquetes VSIX, pero este comportamiento está diseñado principalmente para fines de depuración. Al implementar una aplicación de Shell, debe utilizar paquetes MSI para permitir para acceder al registro y para los reinicios durante la instalación. Para preparar la aplicación para la implementación de MSI, realice los pasos siguientes.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Para preparar una aplicación de Shell para la implementación de MSI  
  
1.  Editar cada archivo .vsixmanifest en la solución.  
  
     En el `Identifier` elemento, agregue un `InstalledByMSI` elemento y un `SystemComponent` elemento y, a continuación, establezca sus valores en `true`.  
  
     Estos elementos impedir que el instalador VSIX intentando instalar los componentes y el usuario de desinstalar usando la **extensiones y actualizaciones** cuadro de diálogo.  
  
2.  Para cada proyecto que contiene un manifiesto VSIX, edite las tareas de compilación para generar el contenido a la ubicación desde la que se instalará el MSI. Incluir el manifiesto de VSIX en la salida de compilación, pero no se compilan un archivo. vsix.  
  
## <a name="creating-an-msi-for-your-shell"></a>Crear un archivo MSI del shell  
 Para compilar el paquete MSI, se recomienda que realice la [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) porque ofrece mayor flexibilidad que un proyecto de instalación estándar.  
  
 En el archivo Product.wxs, establezca los bloques de detección y el diseño de componentes de Shell.  
  
 A continuación, cree las entradas del registro, en el archivo .reg para su solución y en ApplicationRegistry.wxs.  
  
### <a name="detection-blocks"></a>Bloques de detección  
 Un bloque de detección se compone de un `Property` elemento que especifica un requisito previo para detectar y un `Condition` elemento que especifica un mensaje que se devuelve si el requisito previo no está presente en el equipo. Por ejemplo, la aplicación de Shell requiere Microsoft Visual Studio Shell redistributable, y el bloque de detección tendrá un aspecto similar el siguiente marcado.  
  
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
 Debe agregar elementos para identificar la estructura de directorios de destino y los componentes que desea instalar.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Para establecer el diseño de componentes de Shell  
  
1.  Crear una jerarquía de `Directory` elementos para representar todos los directorios para crear en el sistema de archivos en el equipo de destino, como se muestra en el ejemplo siguiente.  
  
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
  
2.  Identificar los componentes que requieren el Shell y la aplicación de Shell, como se muestra en el ejemplo siguiente.  
  
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
  
    1.  El `ComponentRef` elemento hace referencia a otro archivo wxs que identifica los archivos que requiera el componente actual. Por ejemplo, GeneralProfile tiene la siguiente definición en HelpAbout.wxs.  
  
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
  
         El `DirectoryRef` elemento especifica dónde de estos archivos en el equipo del usuario. El `Directory` elemento especifica que se va a instalar en un subdirectorio y cada uno de ellos `File` elemento representa un archivo que se compila o que existe como parte de la solución e identifica donde se puede encontrar ese archivo cuando se crea el archivo MSI.  
  
    2.  El `ComponentGroupRef` elemento hace referencia a un grupo de otros componentes (o componentes y grupos de componentes). Por ejemplo, `ComponentGroupRef` en ApplicationGroup se define como sigue en Application.wxs.  
  
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
    >  Requiere las dependencias para las aplicaciones de Shell (aislado) son: DebuggerProxy, MasterPkgDef, recursos (especialmente en el archivo de .winprf), la aplicación y PkgDefs.  
  
### <a name="registry-entries"></a>Entradas del Registro  
 La plantilla de proyecto de Shell (aislado) incluye un *ProjectName*archivo .reg para las claves del registro combinar en la instalación. Estas entradas del registro deben formar parte de MSI para la instalación y con fines de limpieza. También debe crear bloques de registro correspondiente en ApplicationRegistry.wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Para integrar las entradas del registro en el archivo MSI  
  
1.  En el **Shell personalización** carpeta, abra *ProjectName*. reg.  
  
2.  Reemplace todas las instancias del token de $ $RootFolder por la ruta de acceso del directorio de instalación de destino.  
  
3.  Agregue las entradas de registro que requiera la aplicación.  
  
4.  Abra ApplicationRegistry.wxs.  
  
5.  Para cada entrada del registro de *ProjectName*. reg, agregar un bloque de registro correspondientes, como se muestran en los ejemplos siguientes.  
  
    |*ProjectName*. reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "PhotoStudio DTE Object"|\<Id. de RegistryKey = raíz 'DteClsidRegKey' = 'HKCR' Key =' $(var.) DteClsidRegKey)' acción = 'createAndRemoveOnUninstall' ><br /><br /> \<Tipo de RegistryValue = 'string' Name =' @' valor =' $(var.) Objeto ShortProductName) DTE "/ ><br /><br /> \</ RegistryKey >|  
    |[HKEY_CLASSES_ROOT\CLSID\\\LocalServer32 {bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "$RootFolder$\PhotoStudio.exe"|\<Id. de RegistryKey = raíz 'DteLocSrv32RegKey' = 'HKCR' Key =' $(var.) DteClsidRegKey) \LocalServer32' acción = 'createAndRemoveOnUninstall' ><br /><br /> \<Tipo de RegistryValue = 'string' Name =' @' valor ='[INSTALLDIR] $(var.) ShortProductName) .exe "/ ><br /><br /> \</ RegistryKey >|  
  
     En este ejemplo, Var.DteClsidRegKey se resuelve como la clave del registro en la fila superior. Var.ShortProductName se resuelve como `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Crear a un programa previo de instalación  
 Se instalará el MSI completado solo si todos los requisitos previos se instalan en primer lugar. Para facilitar la experiencia del usuario final, crear un programa de instalación que se recopila e instala todos los requisitos previos antes de instalar la aplicación. Para garantizar una instalación correcta, lleve a cabo estas acciones:  
  
-   Exigir la instalación mediante el administrador.  
  
-   Detectar si está instalado Visual Studio Shell (aislado).  
  
-   Instaladores de Shell de uno o ambos se ejecutan en orden.  
  
-   Controlar las solicitudes de reinicio.  
  
-   Ejecute el MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Exigir la instalación mediante el administrador  
 Este procedimiento es necesario para habilitar el programa de instalación tener acceso a los directorios necesarios como archivos \Program\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Para exigir la instalación mediante el administrador  
  
1.  Abra el menú contextual del proyecto de instalación y, a continuación, elija **propiedades**.  
  
2.  En **archivo de configuración del vinculador/propiedades/manifiesto**, establezca **nivel de ejecución de UAC** a **requireAdministrator**.  
  
     Esta propiedad hace que el atributo que requiere el programa para ejecutarse como administrador en el archivo de manifiesto incrustado.  
  
### <a name="detecting-shell-installations"></a>Detectar instalaciones de Shell  
 Para determinar si se debe instalar Visual Studio Shell (aislado), determine primero si ya está instalado, compruebe el valor del registro de HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  El bloque de detección de Shell en Product.wxs también se leen estos valores.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder especifica la ubicación donde se instaló el Shell de Visual Studio y puede comprobar si hay archivos en él.  
  
 Para obtener un ejemplo de cómo detectar una instalación de Shell, consulte el `GetProductDirFromReg` función de Utilities.cpp en el ejemplo de implementación de Shell.  
  
 Si uno o ambos de los Shells de Visual Studio que necesita el paquete no está instalado en el equipo, debe agregarlos a la lista de componentes que desea instalar. Para obtener un ejemplo, vea el `ComponentsPage::OnInitDialog` función de ComponentsPage.cpp en el ejemplo de implementación de Shell.  
  
### <a name="running-the-shell-installers"></a>Ejecuta a los instaladores de Shell  
 Para ejecutar a los instaladores de Shell, llame a los archivos redistribuibles de Visual Studio Shell mediante el uso de los argumentos de línea de comandos correctos. Como mínimo, debe usar los argumentos de línea de comandos **/q /norestart** y espere a que el código de retorno determinar qué se debe hacer a continuación. En el ejemplo siguiente se ejecuta el paquete redistribuible Shell (aislado).  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Ejecuta a los instaladores de paquete de idioma de Shell  
 Si se encuentra en su lugar que tenga instalados el shell o shells y solo necesita un paquete de idioma de, puede instalar los paquetes de idioma como se muestra en el ejemplo siguiente.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Descifrar valores devueltos  
 En algunos sistemas operativos, la instalación de Visual Studio Shell (aislado) requerirá un reinicio. Esta condición se puede determinar mediante el código de retorno de la llamada a `ExecCmd`.  
  
|Valor devuelto|Descripción|  
|------------------|-----------------|  
|ERROR_SUCCESS|Se completó la instalación. Ahora puede instalar la aplicación.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Se completó la instalación. Puede instalar la aplicación después de reiniciar el equipo.|  
|3015|Instalación está en curso. Se requiere un reinicio del equipo para continuar la instalación.|  
  
### <a name="handling-restarts"></a>Control de reinicio  
 Cuando ejecutó el programa de instalación de Shell mediante el uso de la **/norestart** argumento, se especifica que no reinicie el equipo o solicitar que se reinicie el equipo. Sin embargo, podría ser necesario reiniciar, y debe asegurarse de que el instalador continúa después de reiniciar el equipo.  
  
 Para controlar correctamente los reinicios, asegúrese de que sólo un programa de instalación está establecido en reanudar y que el proceso de reanudación se administrarán correctamente.  
  
 Si se devuelve ERROR_SUCCESS_REBOOT_REQUIRED o 3015, el código debe reiniciar el equipo antes de continuar la instalación.  
  
 Para controlar los reinicios, lleve a cabo estas acciones:  
  
-   Configurar el registro para reanudar la instalación cuando se inicie Windows.  
  
-   Realizar un reinicio del doble del arranque.  
  
-   Elimine la clave de ResumeData de instalador de Shell.  
  
-   Reinicie Windows.  
  
-   Restablecer la ruta de acceso de inicio de MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Configurar el registro para reanudar el programa de instalación cuando se inicie Windows  
 La clave del registro HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ se ejecuta al iniciarse el sistema con permisos administrativos y, a continuación, se borra. HKEY_CURRENT_USER contiene una clave similar, pero se ejecuta como un usuario normal y no es adecuada para las instalaciones. Puede reanudar la instalación de contar con un valor de cadena de la clave de RunOnce que llama el programa de instalación. Sin embargo, se recomienda que llame el programa de instalación mediante un **/reiniciar** o parámetro similar para notificar a la aplicación que está reanudando en lugar de iniciarse. También puede incluir parámetros para indicar dónde se encuentre en el proceso de instalación, que es especialmente útil en las instalaciones que pueden requerir varios reinicios.  
  
 En el ejemplo siguiente se muestra un valor de clave de registro RunOnce para reanudar una instalación.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Reiniciar el doble de programa previo de instalación  
 Si se usa el programa de instalación directamente desde RunOnce, el escritorio no podrá cargar completamente. Para disponer de la interfaz de usuario completo, debe crear otra ejecución del programa de instalación y finalizar la instancia de RunOnce.  
  
 Volver a debe ejecutar el programa de instalación para que obtiene los permisos correctos, y debe proporcionar suficiente información para saber dónde se detuvo antes del reinicio, como se muestra en el ejemplo siguiente.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Al eliminar la clave de ResumeData de instalador de Shell  
 El instalador del Shell establece la clave del registro de HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData con datos que se va a reanudar la instalación después del reinicio. Dado que está reanudando la aplicación, no el instalador del Shell, eliminar esa clave del registro, como se muestra en el ejemplo siguiente.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Reinicio de Windows  
 Después de establecer las claves del registro necesarias, puede reiniciar Windows. En el ejemplo siguiente se invoca los comandos de reinicio para distintos sistemas operativos Windows.  
  
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
 Antes de reiniciar, el directorio actual es la ubicación de su programa de instalación, pero después del reinicio, la ubicación, se convierte en el directorio system32. El programa de instalación debe restablecer el directorio actual antes de cada llamada MSI, como se muestra en el ejemplo siguiente.  
  
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
 Después de que el instalador de Visual Studio Shell devuelve ERROR_SUCCESS, puede ejecutar el archivo MSI para la aplicación. Dado que el programa de instalación proporciona la interfaz de usuario, iniciar el MSI en modo silencioso (**/q**) y con el registro (**/l**), como se muestra en el ejemplo siguiente.  
  
```cpp  
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
 [Tutorial: creación una aplicación básica de Shell aislado](walkthrough-creating-a-basic-isolated-shell-application.md)