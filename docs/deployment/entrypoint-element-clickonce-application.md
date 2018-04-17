---
title: '&lt;punto de entrada&gt; elemento (aplicación ClickOnce) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: cd263d8137b380519477d16079e8ed8b1547fbbe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;punto de entrada&gt; elemento (aplicación ClickOnce)
Identifica el ensamblado que se debe ejecutar cuando esto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se ejecuta en un equipo cliente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `entryPoint` es obligatorio y se encuentra en el espacio de nombres `urn:schemas-microsoft-com:asm.v2`. Solo puede haber una `entryPoint` elemento definido en un manifiesto de aplicación.  
  
 El `entryPoint` elemento tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`name`|Opcional. Este valor no se utiliza por .NET Framework.|  
  
 `entryPoint` tiene los siguientes elementos.  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Requerido. El rol de `assemblyIdentity` y sus atributos se definen en [ \<assemblyIdentity > elemento](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 El `processorArchitecture` atributo de este elemento y el `processorArchitecture` atributo definido en el `assemblyIdentity` en otra parte en la aplicación manifiesto debe coincidir.  
  
## <a name="commandline"></a>Línea de comandos  
 Requerido. Debe ser un elemento secundario de la `entryPoint` elemento. No tiene elementos secundarios y tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`file`|Requerido. Una referencia local al ensamblado de inicio para el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Este valor no puede contener la barra diagonal (/) o barra diagonal inversa (\\) separadores de ruta de acceso.|  
|`parameters`|Requerido. Describe la acción que se realizará con el punto de entrada. El único valor válido es `run`; si se proporciona una cadena en blanco, `run` se da por hecho.|  
  
## <a name="customhostrequired"></a>customHostRequired  
 Opcional. Si se incluye, especifica que esta implementación contiene un componente que se va a implementar dentro de un host personalizado y no es una aplicación independiente.  
  
 Si este elemento está presente, el `assemblyIdentity` y `commandLine` elementos no también deben estar presentes. Si lo son, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , se producirá un error de validación durante la instalación.  
  
 Este elemento no tiene atributos y ningún elemento secundario.  
  
## <a name="customux"></a>customUX  
 Opcional. Especifica que la aplicación está instalada y mantiene un instalador personalizado y no crear una entrada de menú Inicio, acceso directo o agregar o quitar programas.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Una aplicación que incluye el elemento customUX debe proporcionar un instalador personalizado que utiliza el <xref:System.Deployment.Application.InPlaceHostingManager> clase para realizar operaciones de instalación. No se puede instalar una aplicación con este elemento haciendo doble clic en su manifiesto o setup.exe requisitos previos del programa previo. El instalador personalizado puede crear entradas del menú Inicio, accesos directos y entradas de agregar o quitar programas. Si el instalador personalizado no crea una entrada agregar o quitar programas, debe almacenar el identificador de suscripción proporcionado por el <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> propiedad y permiten al usuario para desinstalar la aplicación más adelante mediante una llamada a la <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> método. Para obtener más información, consulte [Tutorial: crear un instalador personalizado para una aplicación ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## <a name="remarks"></a>Comentarios  
 Este elemento identifica el ensamblado y punto de entrada para el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  
  
 No se puede utilizar `commandLine` que pasar parámetros a la aplicación en tiempo de ejecución. Puede tener acceso a los parámetros de cadena de consulta para un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación de la aplicación <xref:System.AppDomain>. Para obtener más información, consulte [Cómo: recuperar información de cadena de consulta en una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra un `entryPoint` elemento en un manifiesto de aplicación para una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Este ejemplo de código forma parte de un ejemplo mayor proporcionado para el [manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md) tema.  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)