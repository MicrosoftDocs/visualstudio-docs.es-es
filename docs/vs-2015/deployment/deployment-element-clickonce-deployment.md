---
title: '&lt;Deployment &gt; (elemento, implementación ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a55b5519d5abb7b40aeca23fed1bc2f8ea2cc33d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194640"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;Deployment &gt; (elemento, implementación de ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica los atributos utilizados para la implementación de actualizaciones y la exposición del sistema.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
 El elemento `deployment` es obligatorio y se encuentra en el espacio de nombres `urn:schemas-microsoft-com:asm.v1` . El elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`install`|Necesario. Especifica si esta aplicación define una presencia en el menú **Inicio** de Windows y en la aplicación **Agregar o quitar programas** del panel de control. Los valores válidos son `true` y `false`. Si `false` , [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] siempre ejecutará la versión más reciente de esta aplicación desde la red y no reconocerá el `subscription` elemento.|  
|`minimumRequiredVersion`|Opcional. Especifica la versión mínima de esta aplicación que se puede ejecutar en el cliente. Si el número de versión de la aplicación es menor que el número de versión proporcionado en el manifiesto de implementación, la aplicación no se ejecutará. Los números de versión se deben especificar con el formato `N.N.N.N` , donde `N` es un entero sin signo. Si el `install` atributo es `false` , `minimumRequiredVersion` no se debe establecer.|  
|`mapFileExtensions`|Opcional. Tiene como valor predeterminado `false`. Si es `true` , todos los archivos de la implementación deben tener una extensión. deploy. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] quitará esta extensión de estos archivos tan pronto como los Descargue del servidor Web. Si publica la aplicación mediante [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , agrega automáticamente esta extensión a todos los archivos. Este parámetro permite que se descarguen todos los archivos de una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación desde un servidor Web que bloquea la transmisión de archivos que terminan en extensiones "no seguras" como. exe.|  
|`disallowUrlActivation`|Opcional. Tiene como valor predeterminado `false`. Si `true` , impide que se inicie una aplicación instalada haciendo clic en la dirección URL o escribiendo la dirección URL en Internet Explorer. Si el `install` atributo no está presente, se omite este atributo.|  
|`trustURLParameters`|Opcional. Tiene como valor predeterminado `false`. Si es `true` , permite que la dirección URL contenga los parámetros de cadena de consulta que se pasan a la aplicación, de forma muy similar a como se pasan los argumentos de línea de comandos a una aplicación de línea de comandos. Para obtener más información, vea [Cómo: recuperar información de la cadena de consulta en una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Si el `disallowUrlActivation` atributo es `true` , `trustUrlParameters` se debe excluir del manifiesto o establecerse explícitamente en `false` .|  
  
 El `deployment` elemento también contiene los siguientes elementos secundarios.  
  
## <a name="subscription"></a>subscription  
 Opcional. Contiene el `update` elemento. El elemento `subscription` no tiene atributos. Si el `subscription` elemento no existe, la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación nunca buscará actualizaciones. Si el `install` atributo del `deployment` elemento es `false` , `subscription` se omite el elemento, porque una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación que se inicia desde la red siempre usa la versión más reciente.  
  
## <a name="update"></a>update  
 Necesario. Este elemento es un elemento secundario del `subscription` elemento y contiene el `beforeApplicationStartup` `expiration` elemento o. `beforeApplicationStartup` y `expiration` no se pueden especificar en el mismo manifiesto de implementación.  
  
 El elemento `update` no tiene atributos.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 Opcional. Este elemento es un elemento secundario del `update` elemento y no tiene atributos. Cuando el `beforeApplicationStartup` elemento existe, la aplicación se bloqueará al [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] comprobar si hay actualizaciones, si el cliente está en línea. Si este elemento no existe, buscará [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] primero las actualizaciones en función de los valores especificados para el `expiration` elemento. `beforeApplicationStartup` y `expiration` no se pueden especificar en el mismo manifiesto de implementación.  
  
## <a name="expiration"></a>expiration  
 Opcional. Este elemento es un elemento secundario del `update` elemento y no tiene elementos secundarios. `beforeApplicationStartup` y `expiration` no se pueden especificar en el mismo manifiesto de implementación. Cuando se realiza la comprobación de la actualización y se detecta una versión actualizada, la nueva versión se almacena en caché mientras se ejecuta la versión existente. A continuación, la nueva versión se instala en el siguiente inicio de la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación.  
  
 El `expiration` elemento admite los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`maximumAge`|Necesario. Identifica la antigüedad de la actualización actual antes de que la aplicación realice una comprobación de actualización. El atributo determina la unidad de tiempo `unit` .|  
|`unit`|Necesario. Identifica la unidad de tiempo para `maximumAge` . Las unidades válidas son `hours` , `days` y `weeks` .|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 En el .NET Framework 2,0, este elemento es necesario si el manifiesto de implementación contiene una `subscription` sección. En el .NET Framework 3,5 y versiones posteriores, este elemento es opcional y tomará como valor predeterminado el servidor y la ruta de acceso del archivo en el que se detectó el manifiesto de implementación.  
  
 Este elemento es un elemento secundario del elemento `deployment` y tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`codebase`|Necesario. Identifica la ubicación, como un identificador uniforme de recursos (URI), del manifiesto de implementación que se utiliza para actualizar la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación. Este elemento también permite el reenvío de ubicaciones de actualización para instalaciones basadas en CD. Debe ser un URI válido.|  
  
## <a name="remarks"></a>Comentarios  
 Puede configurar la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación para que busque actualizaciones en el inicio, busque actualizaciones después del inicio o no compruebe nunca si hay actualizaciones. Para buscar actualizaciones en el inicio, asegúrese de que el `beforeApplicationStartup` elemento existe en el `update` elemento. Para buscar actualizaciones después del inicio, asegúrese de que el `expiration` elemento existe en el `update` elemento y que se proporcionan intervalos de actualización.  
  
 Para deshabilitar la comprobación de actualizaciones, quite el `subscription` elemento. Cuando se especifica en el manifiesto de implementación para no buscar nunca actualizaciones, todavía puede comprobar manualmente si hay actualizaciones mediante el <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> método.  
  
 Para obtener más información sobre cómo se relaciona deploymentProvider con las actualizaciones, vea [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo de código siguiente se muestra un `deployment` elemento en un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifiesto de implementación. En el ejemplo se usa un `deploymentProvider` elemento para indicar la ubicación de actualización preferida.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)
