---
title: "Importaci&#243;n de la configuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuración de usuario [SDK de Visual Studio], importar mediante Managed Package Framework"
  - "configuración del IDE, importar mediante Managed Package Framework"
  - "IDE, importar configuración mediante Managed Package Framework"
  - "Managed Package Framework, importar configuración de entorno"
ms.assetid: 943f9a5b-c5a5-45ce-a5a9-8d4c02f15577
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# Importaci&#243;n de la configuraci&#243;n
El entorno de desarrollo integrado \(IDE\) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usa las clases que implementan la interfaz <xref:Microsoft.VisualStudio.Shell.IProfileManager> y están registradas para admitir una implementación de VSPackage. Esta implementación se usa para recuperar el estado de un VSPackage.  
  
 Dado que el IDE crea una instancia de la clase que implementa la interfaz <xref:Microsoft.VisualStudio.Shell.IProfileManager> para admitir la configuración de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la interfaz <xref:Microsoft.VisualStudio.Shell.IProfileManager> debe implementarse en una clase independiente.  
  
> [!NOTE]
>  No implemente <xref:Microsoft.VisualStudio.Shell.IProfileManager> en la clase que implementa <xref:Microsoft.VisualStudio.Shell.Package>.  
  
### Para implementar la exportación de configuración  
  
1.  Declare la clase que implementa la configuración de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Declare que una clase implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager> y proporciónele un `GUID`.  
  
    > [!NOTE]
    >  Las clases que implementan la interfaz <xref:Microsoft.VisualStudio.Shell.IProfileManager> también debe implementar la interfaz <xref:System.ComponentModel.IComponent>, lo que puede realizar derivando la clase de la clase <xref:System.ComponentModel.Component>.  
  
     Por ejemplo:  
  
    ```  
    [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class MyPackageProfileManager : Component, IProfileManager   
    ```  
  
2.  Asegúrese de que la clase que implementa la configuración recupera los datos de estado del disco.  
  
     Este paso se realiza mediante la implementación del método <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A>.  
  
     La información exacta que debe conservarse y cómo se obtendrá y serializará desde el VSPackage es diferente para cada VSPackage.  
  
     Independientemente de la información que deba conservar el VSPackage, la clase que implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager> debe usar la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> suministrada para recuperar datos del archivo de configuración.  
  
     Normalmente, como en el ejemplo siguiente, <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> también valida los datos recuperados y actualiza el estado del VSPackage.  
  
    ```vb#  
    Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
    If mySvc IsNot Nothing Then   
        Dim value As String   
        Dim myState As StateObject = mySvc.MyPackage.packageState   
        reader.ReadSettingString("PbrsShowDesc", value)   
        If value Is Nothing OrElse value = "" Then   
            reader.ReportError("Unable to Help Visibility Setting")   
        Else   
            myState.HelpVisible = Not value.Equals("0")   
        End If   
        reader.ReadSettingString("PbrsAlpha", value)   
        If value Is Nothing OrElse value = "" Then   
            reader.ReportError("Unable to Retrieve Sort Value")   
        Else   
            If Not value.Equals("0") Then   
                myState.SortState = SortState.Alphabetical   
            Else   
                myState.SortState = SortState.Categorized   
            End If   
        End If   
    End If  
    ```  
  
    ```c#  
    MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
    if (mySvc != null){  
      string value;  
      StateObject myState = mySvc.MyPackage.packageState;  
      reader.ReadSettingString("PbrsShowDesc", out value);  
      if (value == null || value == ""){  
          reader.ReportError("Unable to Help Visibility Setting");  
      }else{  
          myState.HelpVisible = !value.Equals("0");  
      }  
      reader.ReadSettingString("PbrsAlpha", out value);  
      if (value == null || value == ""){  
          reader.ReportError("Unable to Retrieve Sort Value");  
      }else{  
        if (!value.Equals("0")){  
          myState.SortState = SortState.Alphabetical;  
        }else{  
          myState.SortState = SortState.Categorized;  
        }  
      }  
    }  
    ```  
  
     Detalles de la implementación:  
  
    -   Vuelva a notificar los errores al usuario de forma interactiva a través del IDE mediante el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReportError%2A> de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>:  
  
        ```vb#  
        reader.ReadSettingString("PbrsAlpha", value)   
        If value Is Nothing OrElse value = "" Then   
            reader.ReportError("Unable to Retrieve Sort Value")   
        End If  
        ```  
  
        ```c#  
          reader.ReadSettingString("PbrsAlpha", out value);  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }  
        ```  
  
    -   Antes de recuperar realmente la configuración almacenada, una implementación del método <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> debería usar el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> para comprobar que la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que exporta la configuración almacenada es compatible.  
  
         En el caso del ejemplo siguiente, la implementación comprueba si la configuración la generó una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con un número de versión principal de `m_supportVer` y, si no es así, indica un error.  
  
        ```vb#  
        If pnMajor <> m_supportVer Then   
            reader.ReportError("Unsupported Version")   
        End If  
        ```  
  
        ```c#  
        if (pnMajor != m_supportVer){  
          reader.ReportError("Unsupported Version");  
        }  
        ```  
  
    -   El archivo de configuración de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] admite el acceso a datos aleatorio, por lo que el orden de lectura y escritura de las operaciones de configuración no es importante. En el ejemplo siguiente, el orden de las operaciones de escritura en la implementación del método <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> es opuesto al de las operaciones de lectura del método <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A>.  
  
    -   El valor del argumento `pszSettingName` proporcionado a un método de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> debe identificar de manera exclusiva cada elemento de datos guardado en una categoría de configuración.  
  
        > [!NOTE]
        >  Los nombres deben ser únicos solo dentro del ámbito de la clase de implementación porque el IDE usa el GUID de la clase que implementa la configuración y el valor de `pszSettingName` para identificar cada opción de configuración guardada. Si se invoca más de un método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> con el mismo valor de `pszSettingName`, el valor original se sobrescribirá en el archivo de configuración.  
  
3.  Garantice la coherencia entre el estado de VSPackage y la configuración almacenada localmente o en caché.  
  
     Este paso se realiza normalmente durante la implementación del método <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> \(como se muestra en el ejemplo siguiente\). Los detalles de este paso son específicos de un VSPackage y pueden implicar obtener el estado de VSPackage a través de la automatización, la consulta del VSPackage y la definición de las claves del Registro.  
  
    > [!NOTE]
    >  El método <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> debe recuperar la información guardada por el método <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> cuando el IDE llama al método <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> durante la inicialización del VSPackage que admite.  
  
     En el ejemplo siguiente, la clase que proporciona compatibilidad de configuración implementa el método <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> para:  
  
    -   Obtener acceso a la información de estado actualizada del VSPackage.  
  
        ```vb#  
        Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
        Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
        Dim rootKey As RegistryKey = package.UserRegistryRoot  
        ```  
  
        ```c#  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        Package package = GetService(typeof(Package)) as Package;  
        RegistryKey rootKey = package.UserRegistryRoot;  
        ```  
  
    -   Usar esa información para actualizar la configuración del Registro del VSPackage.  
  
        ```vb#  
        If mySvc.MyPackage.packageState IsNot Nothing Then   
            Using rootKey   
                Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                    Using pbrsKey   
                        DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                    End Using   
                End Using   
            End Using   
        End If  
        ```  
  
        ```c#  
        if (mySvc.MyPackage.packageState != null) {  
          using (rootKey) {  
            using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
              using (pbrsKey) {  
                ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
              }  
            }  
          }  
        }  
        ```  
  
    -   > [!NOTE]
        >  La división del trabajo entre los métodos <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> y <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> depende de la implementación y es, en cierto modo, arbitraria. Por ejemplo, se podría reescribir la implementación con una implementación vacía del método <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> y todas las consultas de estado y del Registro se podrían realizar en el método <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A>.  
  
4.  Registre la clase que implementa la configuración de manera que indique que proporciona soporte para un VSPackage.  
  
     Aplique una instancia del <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> construido mediante el <xref:System.Type> de la clase que implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager> en la implementación de <xref:Microsoft.VisualStudio.Shell.Package> del VSPackage.  
  
    ```vb#  
    <ProvideProfile(GetType(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, False)> _   
    <Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
    Class MyPackage   
        Inherits Package   
    End Class  
    ```  
  
    ```c#  
     [ProvideProfile(typeof(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, false)]  
    [Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
    class MyPackage: Package   
    ```  
  
     En este caso, el atributo indica al IDE que la clase `MyPackageProfileManager` proporciona una implementación de configuración a la clase `MyPackage`. El punto de la configuración personalizada del Registro se crea en HKLM\\Software\\Microsoft\\VisualStudio\\*\<versión\>*\\UserSettings\\ CoreUI\_MyPackage, donde *\<versión\>* es la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por ejemplo 8.0.  
  
     Para obtener más información, vea [Compatibilidad con la configuración de usuario](../extensibility/internals/support-for-user-settings.md) y <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Ejemplo  
 En el ejemplo siguiente se implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager> en una clase.  
  
```vb#  
Imports System   
Imports System.Runtime.InteropServices   
Imports Microsoft.VisualStudio.Shell   
Imports Microsoft.VisualStudio.Shell.Interop   
Imports Microsoft.Win32   
Imports myPackageNameSpace   
Namespace myProfileManagerNameSpace  
  
    <Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Friend Class MyPackageProfileManager   
        Inherits System.ComponentModel.Component   
        Implements IProfileManager   
        Friend Const m_supportVer As Integer = 8   
        Public Sub SaveSettingsToXml(ByVal writer As IVsSettingsWriter)   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
            If mySvc IsNot Nothing Then   
                ' Information is stored in a StateObject.   
                Dim myState As StateObject = mySvc.MyPackage.packageState   
                writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
                writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromXml(ByVal reader As IVsSettingsReader)   
  
            Dim pnMajor As Integer, pnMinor As Integer, pnBuild As Integer   
            ' First check if we are getting data from the correct major version.   
            reader.ReadVersion(pnMajor, pnMinor, pnBuild)   
            If pnMajor <> m_supportVer Then   
                reader.ReportError("Unsupported Version")   
            Else   
                Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
                If mySvc IsNot Nothing Then   
                    Dim value As String   
                    Dim myState As StateObject = mySvc.MyPackage.packageState   
                    reader.ReadSettingString("PbrsShowDesc", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Help Visibility Setting")   
                    Else   
                        myState.HelpVisible = Not value.Equals("0")   
                    End If   
                    reader.ReadSettingString("PbrsAlpha", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Retrieve Sort Value")   
                    Else   
                        If Not value.Equals("0") Then   
                            myState.SortState = SortState.Alphabetical   
                        Else   
                            myState.SortState = SortState.Categorized   
                        End If   
                    End If   
                End If   
            End If   
        End Sub   
  
        Public Sub SaveSettingsToStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
  
            If mySvc.MyPackage.packageState IsNot Nothing Then   
                Using rootKey   
                    Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                        Using pbrsKey   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        End Using   
                    End Using   
                End Using   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
            Using rootKey   
                Dim pbrsKey As RegistryKey = rootKey.OpenSubKey(Me.[GetType]().Name)   
                If pbrsKey IsNot Nothing Then   
                    Using pbrsKey   
                        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        Else   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
                        End If   
                    End Using   
                End If   
            End Using   
        End Sub   
    End Class   
End Namespace  
  
```  
  
```c#  
namespace myProfileManagerNameSpace  {  
  
  using System;  
  using System.Runtime.InteropServices;  
  using Microsoft.VisualStudio.Shell;  
  using Microsoft.VisualStudio.Shell.Interop;  
  using Microsoft.Win32;  
  using myPackageNameSpace;  
  
  [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
  internal class MyPackageProfileManager : System.ComponentModel.Component , IProfileManager {  
    internal const int m_supportVer = 8;  
    public void SaveSettingsToXml(IVsSettingsWriter writer) {  
      MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
      if (mySvc != null) {  
        // Information is stored in a StateObject.  
        StateObject myState = mySvc.MyPackage.packageState;  
        writer.WriteSettingString(   
                                  "PbrsAlpha",   
                                  (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
        writer.WriteSettingString(   
                                  "PbrsShowDesc",   
                                  (myState.HelpVisible ? "1" : "0"));  
      }  
    }  
  
    public void LoadSettingsFromXml(IVsSettingsReader reader)  
    {  
  
      int pnMajor, pnMinor, pnBuild;  
      // First check if we are getting data from the correct major version.   
      reader.ReadVersion(pnMajor, pnMinor, pnBuild);  
      if (pnMajor != m_supportVer){  
        reader.ReportError("Unsupported Version");  
      }else{  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        if (mySvc != null){  
          string value;  
          StateObject myState = mySvc.MyPackage.packageState;  
          reader.ReadSettingString("PbrsShowDesc", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Help Visibility Setting");  
          }else{  
            myState.HelpVisible = !value.Equals("0");  
          }  
          reader.ReadSettingString("PbrsAlpha", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }else{  
            if (!value.Equals("0")){  
              myState.SortState = SortState.Alphabetical;  
            }else{  
              myState.SortState = SortState.Categorized;  
            }  
          }  
        }  
      }  
    }  
  
    public void SaveSettingsToStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
  
      if (mySvc.MyPackage.packageState != null) {  
        using (rootKey) {  
          using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
            using (pbrsKey) {  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  
    public void LoadSettingsFromStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
      using (rootKey) {  
        RegistryKey pbrsKey = rootKey.OpenSubKey(this.GetType().Name);  
        if (pbrsKey != null) {  
          using (pbrsKey) {  
            if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }else{  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.IProfileManager>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>   
 [Exportación de configuración](../misc/exporting-settings.md)   
 [Compatibilidad con la configuración de usuario](../extensibility/internals/support-for-user-settings.md)