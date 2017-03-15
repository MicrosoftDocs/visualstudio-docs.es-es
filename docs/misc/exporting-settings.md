---
title: "Exportaci&#243;n de configuraci&#243;n | Microsoft Docs"
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
  - "IDE, exportar configuración mediante Managed Package Framework"
  - "Managed Package Framework, exportar configuración de entorno"
  - "configuración de usuario [SDK de Visual Studio], importar mediante Managed Package Framework"
  - "configuración del IDE, exportar mediante Managed Package Framework"
ms.assetid: cb3ddb38-4e75-4f05-a83a-8396345bc36c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Exportaci&#243;n de configuraci&#243;n
El entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utiliza las clases que implementan la interfaz y las clases de <xref:Microsoft.VisualStudio.Shell.IProfileManager> registrados como admitir una implementación determinada de Paquete que guardar el estado de un paquete VSPackage.  
  
 Porque el IDE crea instancias de la clase que implementa la interfaz de <xref:Microsoft.VisualStudio.Shell.IProfileManager> para admitir los valores, <xref:Microsoft.VisualStudio.Shell.IProfileManager> se debe implementar en una clase independiente.  
  
> [!NOTE]
>  no implemente <xref:Microsoft.VisualStudio.Shell.IProfileManager> en la clase que implementa <xref:Microsoft.VisualStudio.Shell.Package>.  
  
### para implementar la exportación de valores  
  
1.  declare la clase que implementa los valores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
     Declare una clase como implementar la interfaz de <xref:Microsoft.VisualStudio.Shell.IProfileManager> y proporcionela con un GUID.  
  
    > [!NOTE]
    >  Las clases que implementan <xref:Microsoft.VisualStudio.Shell.IProfileManager> también deben implementar <xref:System.ComponentModel.IComponent>.  Esto se puede hacer derivando una clase de <xref:System.ComponentModel.Component>.  
  
     Por ejemplo:  
  
    ```  
    [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class MyPackageProfileManager : Component, IProfileManager   
    ```  
  
2.  Asegúrese de que la clase que implementa los valores obtiene la información de estado correcto.  Este procedimiento es específico para cada Paquete, y puede incluir obtener el estado de automatización, consultando las claves del Registro, o consultando el paquete VSPackage.  
  
     Normalmente, como en el ejemplo siguiente, utilice la implementación del método de <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> para validar y la información de estado de VSPackage de la fase.  
  
    > [!NOTE]
    >  El método de <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> también llama el IDE cuando se inicializa el Paquete que admite.  
  
     En este caso, la implementación del método de <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> hace:  
  
    -   Obtiene acceso a la información de estado en la configuración y la información de configuración actuales de VSPackage almacenadas en el registro.  
  
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
  
    -   Dependiendo del valor devuelto por el método de `MakeCurrentSettingTheDefault` de VSPackage, actualiza los valores del registro mediante el estado actual de VSPackage, o el estado utilizando los valores del registro.  
  
        ```vb#  
        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
        Else   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
        End If  
        ```  
  
        ```c#  
        if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
        }else{  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
        }  
        ```  
  
         Para simplificar en este ejemplo, a menos que el método de `MakeCurrentSettingsTheDefault` devuelve `true`, se restablece el estado actual siempre el valor predeterminado que se almacena en el registro.  
  
3.  Asegúrese de que la clase que implementa los valores también conserva el estado en el disco.  
  
     La escritura real de la información de estado al archivo de disco de los valores se debe realizar siempre a la implementación de la clase de método de <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> .  Los detalles de la operación de programador de los valores dependen de la implementación.  
  
     Sin embargo, la clase debe obtener acceso a la información de estado y utilizar la interfaz proporcionada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> para guardar los datos en el archivo de configuración.  
  
     Normalmente, como en el ejemplo siguiente, la implementación del método de <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> no valida la información de estado.  La validación se realiza en el método de <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> .  En su lugar, la implementación obtiene simplemente el acceso a la información y a las etiquetas de estado y, en este caso, como datos de cadena.  
  
    ```vb#  
    Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
    If mySvc IsNot Nothing Then   
        ' Information is stored in a StateObject   
        Dim myState As StateObject = mySvc.MyPackage.packageState   
        writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
        writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
    End If  
  
    ```  
  
    ```c#  
    MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
    if (mySvc != null) {  
      // Information is stored in a StateObject  
      StateObject myState = mySvc.MyPackage.packageState;  
     writer.WriteSettingString(   
                                "PbrsAlpha",   
                                (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
      writer.WriteSettingString(   
                                "PbrsShowDesc",   
                                (myState.HelpVisible ? "1" : "0"));  
    }  
    ```  
  
     Los detalles de implementación son los siguientes:  
  
    -   Además de los datos explícitamente tipo y transparente a la implementación del método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> , los valores API también guarda la información de versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Por consiguiente, guardado valores puede compararse con la versión del IDE que los generado durante la importación de los valores.  
  
    -   El valor del argumento de `pszSettingName` proporcionado un método de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> debe identificar cada elemento de datos guardado en una categoría de configuración.  
  
        > [!NOTE]
        >  Los nombres deben sólo ser únicos dentro del ámbito de la clase que implementa.  Usa el IDE GUID de la clase que implementa la configuración y el valor de `pszSettingName` para identificar cada valor guardado.  Si se llama más de un método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> que tiene el mismo valor de `pszSettingName` , el valor original se sobrescribe en el archivo de configuración.  
  
    -   El archivo de configuración admite el acceso a datos aleatorios, por lo que el orden de las operaciones de lectura y escritura no es importante.  En el ejemplo siguiente, el orden de las operaciones de programador en la implementación del método de <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> es contrario de las operaciones de lectura en el método de <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> .  
  
    -   Si la implementación puede los datos de mapa en uno de los cuatro formatos admitidos, no existe ninguna restricción en cuánto o lo que se puede escribir el tipo de datos.  
  
        > [!NOTE]
        >  La división del trabajo entre <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> y los métodos de <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> depende de la implementación y es algo arbitraria.  Por ejemplo, la implementación se podría escribir mediante una implementación vacía del método de <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> y haciendo todas las consultas de registro y estado realizar en el método de <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> .  
  
4.  Registre los valores que implementan la clase como proporcionar compatibilidad un VSPackage.  
  
     Aplica una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> que se construyen mediante <xref:System.Type> de la clase que implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager> a la implementación de VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .  
  
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
  
     En este caso, el atributo informa al IDE que la clase de `MyPackageProfileManager` proporciona una implementación de los valores a la clase de `MyPackage` .  El punto de configuración personalizado en el registro se crea en HKLM \\Software\\Microsoft\\VisualStudio \\*versión*\\UserSettings\\ CoreUI\_MyPackage, donde es la versión *versión* de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por ejemplo, 10,0.  
  
     Para obtener más información, vea [Compatibilidad con la configuración de usuario](../extensibility/internals/support-for-user-settings.md) y <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Ejemplo  
 El ejemplo siguiente se implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager> en una clase.  
  
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
            ' First, check if data is obtained from the correct major version   
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
  
Convert C# to VB.NET  
  
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
      // First, check if data is obtained from the correct major version   
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
 [Importación de la configuración](../misc/importing-settings.md)   
 [Compatibilidad con la configuración de usuario](../extensibility/internals/support-for-user-settings.md)