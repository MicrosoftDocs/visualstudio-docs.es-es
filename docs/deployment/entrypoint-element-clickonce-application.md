---
title: '&lt;entryPoint&gt; elemento (aplicación ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e37021c6c8492b0c882a84cbb88fe1cd9b5458e6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950269"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint&gt; elemento (aplicación ClickOnce)
Identifica el ensamblado que se debe ejecutar cuando esto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se ejecuta en un equipo cliente.  

## <a name="syntax"></a>Sintaxis  

```xml  
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
 El elemento `entryPoint` es obligatorio y se encuentra en el espacio de nombres `urn:schemas-microsoft-com:asm.v2` . Solo puede haber un `entryPoint` elemento definido en un manifiesto de aplicación.  

 El elemento `entryPoint` tiene los atributos siguientes:  

|Atributo|Descripción|  
|---------------|-----------------|  
|`name`|Opcional. Este valor no se utiliza por .NET Framework.|  

 `entryPoint` tiene los siguientes elementos:  

## <a name="assemblyidentity"></a>assemblyIdentity  
 Obligatorio. El rol de `assemblyIdentity` y sus atributos se definen en [ \<assemblyIdentity > elemento](../deployment/assemblyidentity-element-clickonce-application.md).  

 El `processorArchitecture` atributo de este elemento y el `processorArchitecture` atributo definido en el `assemblyIdentity` en otra parte en la aplicación de manifiesto debe coincidir.  

## <a name="commandline"></a>commandLine  
 Obligatorio. Debe ser un elemento secundario de la `entryPoint` elemento. No tiene elementos secundarios y tiene los siguientes atributos.  


| Atributo | Descripción |
|--------------| - |
| `file` | Obligatorio. Una referencia local al ensamblado de inicio para el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Este valor no puede contener la barra diagonal (/) o barra diagonal inversa (\\) separadores de ruta de acceso. |
| `parameters` | Obligatorio. Describe la acción que se realiza con el punto de entrada. El único valor válido es `run`; si no se proporciona una cadena en blanco, `run` se da por hecho. |

## <a name="customhostrequired"></a>customHostRequired  
 Opcional. Si se incluye, especifica que esta implementación contiene un componente que se va a implementar dentro de un host personalizado y no es una aplicación independiente.  

 Si este elemento está presente, el `assemblyIdentity` y `commandLine` elementos no también deben estar presentes. Si lo son, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , se producirá un error de validación durante la instalación.  

 Este elemento no tiene atributos y ningún elemento secundario.  

## <a name="customux"></a>customUX  
 Opcional. Especifica que la aplicación está instalada y mantiene un instalador personalizado y no crear una entrada de menú Inicio, acceso directo o agregar o quitar programas.  

```xml  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  

 Una aplicación que incluye el elemento customUX debe proporcionar un instalador personalizado que utiliza el <xref:System.Deployment.Application.InPlaceHostingManager> clase para realizar operaciones de instalación. Una aplicación con este elemento no se puede instalar haciendo doble clic en su manifiesto o setup.exe de arranque de requisitos previos. El instalador personalizado puede crear entradas de agregar o quitar programas, accesos directos y entradas de menú de inicio. Si el instalador personalizado no crea una entrada en Agregar o quitar programas, debe almacenar el identificador de suscripción proporcionado por el <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> propiedad y habilitar al usuario que desinstale la aplicación más adelante mediante una llamada a la <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> método. Para obtener más información, vea [Tutorial: Creación de un instalador personalizado para una aplicación ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  

## <a name="remarks"></a>Comentarios  
 Este elemento identifica el ensamblado y punto de entrada para el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  

 No puede usar `commandLine` para pasar parámetros a la aplicación en tiempo de ejecución. Puede tener acceso a los parámetros de cadena de consulta para un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación de la aplicación <xref:System.AppDomain>. Para obtener más información, vea [Cómo: Recuperación de información de la cadena de consulta de una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  

## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se ilustra un `entryPoint` elemento en un manifiesto de aplicación para un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Este ejemplo de código forma parte de un ejemplo más extenso proporcionado para el [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md) tema.  

```xml  
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
