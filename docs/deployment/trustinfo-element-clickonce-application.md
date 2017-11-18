---
title: "&lt;trustInfo&gt; elemento (aplicación ClickOnce) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 645d4252dd13f4e4629d1ab636ad8b85142242c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="lttrustinfogt-element-clickonce-application"></a>&lt;trustInfo&gt; elemento (aplicación ClickOnce)
Describe los permisos de seguridad mínimos necesarios para que la aplicación se ejecute en el equipo cliente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      <trustInfo>  
   <security>  
      <applicationRequestMinimum>  
         <PermissionSet  
            ID  
            Unrestricted>  
            <IPermission  
               class  
               version  
               Unrestricted  
            />  
         </PermissionSet>  
         <defaultAssemblyRequest  
            permissionSetReference  
         />  
         <assemblyRequest  
            name  
            permissionSetReference  
         />  
      </applicationRequestMinimum>  
      <requestedPrivileges>  
         <requestedExecutionLevel  
            level  
            uiAccess  
         />  
      </requestedPrivileges>  
   </security>  
</trustInfo>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `trustInfo` es obligatorio y se encuentra en el espacio de nombres `asm.v2` . No tiene atributos y contiene los elementos siguientes.  
  
## <a name="security"></a>seguridad  
 Requerido. Este elemento es un elemento secundario del elemento `trustInfo` . Contiene el elemento `applicationRequestMinimum` y no tiene atributos.  
  
## <a name="applicationrequestminimum"></a>applicationRequestMinimum  
 Requerido. Este elemento es un elemento secundario del elemento `security` y contiene los elementos `PermissionSet`, `assemblyRequest`y `defaultAssemblyRequest`. Este elemento no tiene atributos.  
  
## <a name="permissionset"></a>PermissionSet  
 Requerido. Este elemento es un elemento secundario del elemento `applicationRequestMinimum` y contiene el elemento `IPermission` . Este elemento tiene los atributos siguientes.  
  
-   `ID`  
  
     Requerido. Identifica el conjunto de permisos. Este atributo puede ser cualquier valor. Se hace referencia al id. en los atributos `defaultAssemblyRequest` y `assemblyRequest` .  
  
-   `version`  
  
     Requerido. Identifica la versión del permiso. Normalmente, este valor es `1`.  
  
## <a name="ipermission"></a>IPermission  
 Opcional. Este elemento es un elemento secundario del elemento `PermissionSet` . El elemento `IPermission` identifica totalmente una clase de permiso en el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. El elemento `IPermission` tiene los atributos siguientes, pero puede tener atributos adicionales que corresponden a las propiedades de la clase de permiso. Para obtener la sintaxis de un permiso concreto, vea los ejemplos enumerados en el archivo Security.config.  
  
-   `class`  
  
     Requerido. Identifica la clase de permiso por nombre seguro. Por ejemplo, el siguiente código identifica el tipo `FileDialogPermission` .  
  
     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
-   `version`  
  
     Requerido. Identifica la versión del permiso. Normalmente, este valor es `1`.  
  
-   `Unrestricted`  
  
     Requerido. Identifica si la aplicación necesita una concesión sin restricciones de este permiso. Si es `true`, la concesión del permiso es incondicional. Si es `false`, o si este atributo no está definido, se restringe según los atributos específicos del permiso definidos en la etiqueta `IPermission` . Seleccione los permisos siguientes:  
  
    ```  
    <IPermission  
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Read="USERNAME" />  
    <IPermission  
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Unrestricted="true" />  
    ```  
  
     En este ejemplo, la declaración de <xref:System.Security.Permissions.EnvironmentPermission> hace que la aplicación esté restringida a leer solo la variable de entorno USERNAME, mientras que la declaración de <xref:System.Security.Permissions.FileDialogPermission> concede a la aplicación uso sin restricciones de todas las clases <xref:System.Windows.Forms.FileDialog> .  
  
## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest  
 Opcional. Identifica el conjunto de permisos concedido a todos los ensamblados. Este elemento es un elemento secundario del elemento `applicationRequestMinimum` y tiene el siguiente atributo.  
  
-   `permissionSetReference`  
  
     Requerido. Identifica el identificador del conjunto de permisos que es el permiso predeterminado. El conjunto de permisos se declara en el elemento `PermissionSet` .  
  
## <a name="assemblyrequest"></a>assemblyRequest  
 Opcional. Identifica los permisos para un ensamblado concreto. Este elemento es un elemento secundario del elemento `applicationRequestMinimum` y tiene los atributos siguientes.  
  
-   `Name`  
  
     Requerido. Identifica el nombre del ensamblado.  
  
-   `permissionSetReference`  
  
     Requerido. Identifica el identificador del conjunto de permisos que requiere este ensamblado. El conjunto de permisos se declara en el elemento `PermissionSet` .  
  
## <a name="requestedprivileges"></a>requestedPrivileges  
 Opcional. Este elemento es un elemento secundario del elemento `security` y contiene el elemento `requestedExecutionLevel` . Este elemento no tiene atributos.  
  
## <a name="requestedexecutionlevel"></a>requestedExecutionLevel  
 Opcional. Identifica el nivel de seguridad en el que la aplicación solicita que se ejecute. Este elemento no tiene elementos secundarios y tiene los atributos siguientes.  
  
-   `Level`  
  
     Requerido. Indica el nivel de seguridad que está solicitando la aplicación. Los valores posibles son:  
  
     `asInvoker`, que no solicita ningún permiso adicional. Este nivel no requiere solicitudes de confianza adicionales.  
  
     `highestAvailable`, que solicita los permisos más altos disponibles para el proceso primario.  
  
     `requireAdministrator`, que solicita permisos completos de administrador.  
  
     Las aplicaciones de[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] solo se instalarán con un valor de `asInvoker`. La instalación de cualquier otro valor producirá un error.  
  
-   `uiAccess`  
  
     Opcional. Indica si la aplicación requiere acceso a elementos de la interfaz de usuario protegidos. Los valores son `true` o `false`y el predeterminado es false. Solo las aplicaciones firmadas deben tener un valor true.  
  
## <a name="remarks"></a>Comentarios  
 Si una aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] solicita más permisos que los que concede el equipo cliente de forma predeterminada, el Administrador de confianza de Common Language Runtime preguntará al usuario si quiere conceder a la aplicación este nivel elevado de confianza. Si responde que no, no se ejecutará la aplicación; de lo contrario, se ejecutará con los permisos solicitados.  
  
 Todos los permisos solicitados con `defaultAssemblyRequest` y `assemblyRequest` se concederán sin preguntar al usuario si el manifiesto de implementación tiene una licencia de confianza válida.  
  
 Para obtener más información acerca de la elevación de permisos, consulte [proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md). Para obtener más información sobre la implementación de directivas, vea [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="examples"></a>Ejemplos  
 Los siguientes tres ejemplos de código ilustran los elementos `trustInfo` para las zonas de seguridad denominadas predeterminadas (Internet, LocalIntranet y FullTrust) para su uso en un manifiesto de aplicación de la implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .  
  
 El primer ejemplo ilustra el elemento `trustInfo` para los permisos predeterminados disponibles en la zona de seguridad de Internet.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="Internet">  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Access="Open" />  
          <IPermission  
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"  
            Allowed="DomainIsolationByUser"  
            UserQuota="10240" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Flags="Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Window="SafeTopLevelWindows"  
            Clipboard="OwnClipboard" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"   
            Level="SafePrinting" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="Internet" />  
      </applicationRequestMinimum>  
    </security>  
  </trustInfo>  
```  
  
 El segundo ejemplo ilustra el elemento `trustInfo` para los permisos predeterminados disponibles en la zona de seguridad LocalIntranet.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="LocalIntranet">  
          <IPermission  
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Read="USERNAME" />  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Allowed="AssemblyIsolationByUser"  
            UserQuota="9223372036854775807"  
            Expiry="9223372036854775807"  
            Permanent="True" />  
          <IPermission  
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="ReflectionEmit" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="Assertion, Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"  
            Level="DefaultPrinting" />  
          <IPermission  
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />  
      </applicationRequestMinimum>  
    </security>  
</trustInfo>  
```  
  
 El tercer ejemplo ilustra el elemento `trustInfo` para los permisos predeterminados disponibles en la zona de seguridad FullTrust.  
  
```  
<trustInfo>  
  <security>  
    <applicationRequestMinimum>  
      <PermissionSet ID="FullTrust" Unrestricted="true" />  
      <defaultAssemblyRequest permissionSetReference="FullTrust" />  
    </applicationRequestMinimum>  
  </security>  
</trustInfo>  
```  
  
## <a name="see-also"></a>Vea también  
 [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)