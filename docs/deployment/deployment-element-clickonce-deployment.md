---
title: '&lt;implementación&gt; elemento (implementación de ClickOnce) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2e078da7f746460ea17d1a5ac2d83e5ac46dc62
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815537"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;implementación&gt; elemento (implementación de ClickOnce)
Identifica los atributos utilizados para la implementación de actualizaciones y la exposición del sistema.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
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
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `deployment` es obligatorio y se encuentra en el espacio de nombres `urn:schemas-microsoft-com:asm.v1`. El elemento tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`install`|Requerido. Especifica si esta aplicación define una presencia en las ventanas **iniciar** menú y en el Panel de Control **agregar o quitar programas** aplicación. Los valores válidos son `true` y `false`. Si `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] siempre se ejecutará la versión más reciente de esta aplicación desde la red y no reconocerá el `subscription` elemento.|  
|`minimumRequiredVersion`|Opcional. Especifica la versión mínima de esta aplicación que se puede ejecutar en el cliente. Si el número de versión de la aplicación es menor que el número de versión proporcionado en el manifiesto de implementación, no se ejecutará la aplicación. Números de versión deben especificarse en el formato `N.N.N.N`, donde `N` es un entero sin signo. Si el `install` atributo es `false`, `minimumRequiredVersion` no debe establecerse.|  
|`mapFileExtensions`|Opcional. Tiene como valor predeterminado `false`. Si `true`, todos los archivos de la implementación deben tener una extensión. deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se eliminan esta extensión de estos archivos en cuanto descarga desde el servidor Web. Si se publica la aplicación utilizando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], esta extensión se agregará automáticamente a todos los archivos. Este parámetro permite que todos los archivos dentro de un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación se descarguen desde un servidor Web que bloquea la transmisión de archivos que terminan en "unsafe" extensiones como .exe.|  
|`disallowUrlActivation`|Opcional. Tiene como valor predeterminado `false`. Si `true`, impide que una aplicación instalada que se inicia haciendo clic en la dirección URL o escriba la dirección URL en Internet Explorer. Si el `install` atributo no está presente, se omite este atributo.|  
|`trustURLParameters`|Opcional. Tiene como valor predeterminado `false`. Si `true`, permite que la dirección URL incluya parámetros de cadena de consulta que se pasan a la aplicación, cantidad como argumentos de línea de comandos se pasan a una aplicación de línea de comandos. Para obtener más información, consulte [Cómo: recuperar información de cadena de consulta en una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Si el `disallowUrlActivation` atributo es `true`, `trustUrlParameters` deben ser excluidos del manifiesto, o se establece explícitamente en `false`.|  
  
 El `deployment` elemento también contiene los siguientes elementos secundarios.  
  
## <a name="subscription"></a>subscription  
 Opcional. Contiene el `update` elemento. El `subscription` elemento no tiene atributos. Si el `subscription` el elemento no existe, la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación no buscará actualizaciones. Si el `install` atributo de la `deployment` elemento es `false`, el `subscription` se omite el elemento, porque un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación que se inicia desde la red siempre utiliza la versión más reciente.  
  
## <a name="update"></a>actualizar  
 Requerido. Este elemento es un elemento secundario de la `subscription` elemento y contiene el `beforeApplicationStartup` o `expiration` elemento. `beforeApplicationStartup` y `expiration` no pueden especificarse simultáneamente en el mismo manifiesto de implementación.  
  
 El `update` elemento no tiene atributos.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 Opcional. Este elemento es un elemento secundario de la `update` elemento y no tiene atributos. Cuando el `beforeApplicationStartup` elemento existe, la aplicación estará bloqueado cuando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] comprueba si hay actualizaciones, si el cliente está en línea. Si este elemento no existe, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] analizará primero las actualizaciones basadas en los valores especificados para el `expiration` elemento. `beforeApplicationStartup` y `expiration` no pueden especificarse simultáneamente en el mismo manifiesto de implementación.  
  
## <a name="expiration"></a>expiración  
 Opcional. Este elemento es un elemento secundario de la `update` elemento, y no tiene elementos secundarios. `beforeApplicationStartup` y `expiration` no pueden especificarse simultáneamente en el mismo manifiesto de implementación. Cuando se produce la comprobación de actualización y se detecta una versión actualizada, la nueva versión almacena en caché mientras se ejecuta la versión existente. A continuación, instale la nueva versión en el siguiente inicio de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  
  
 El `expiration` elemento es compatible con los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`maximumAge`|Requerido. Identifica la antigüedad que debería estar la actualización actual antes de que la aplicación realice una comprobación de actualizaciones. La unidad de tiempo viene determinada por la `unit` atributo.|  
|`unit`|Requerido. Identifica la unidad de tiempo para `maximumAge`. Unidades válidas son `hours`, `days`, y `weeks`.|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 Para la versión 2.0 de .NET Framework, este elemento es necesario si el manifiesto de implementación contiene un `subscription` sección. Para .NET Framework 3.5 y versiones posteriores, este elemento es opcional y predeterminado será el servidor y la ruta de acceso de archivo en el que se detectó el manifiesto de implementación.  
  
 Este elemento es un elemento secundario del elemento `deployment` y tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`codebase`|Requerido. Identifica la ubicación, como un identificador uniforme de recursos (URI), del manifiesto de implementación que se utiliza para actualizar la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Este elemento también permite reenviar las ubicaciones de actualización para las instalaciones basadas en CD. Debe ser un URI válido.|  
  
## <a name="remarks"></a>Comentarios  
 Puede configurar su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación para buscar actualizaciones en el inicio, busque actualizaciones después del inicio, o no buscar actualizaciones. Para buscar actualizaciones en el inicio, asegúrese de que el `beforeApplicationStartup` elemento existe en el `update` elemento. Para buscar actualizaciones después del inicio, asegúrese de que el `expiration` elemento existe en el `update` elemento y que se proporcionan los intervalos de actualización.  
  
 Para deshabilitar la comprobación de actualizaciones, quite el `subscription` elemento. Cuando se especifica en el manifiesto de implementación para no buscar nunca actualizaciones, puede comprobar manualmente las actualizaciones de utilizando el <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> método.  
  
 Para obtener más información sobre cómo deploymentProvider se relaciona con las actualizaciones, consulte [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo de código siguiente se muestra un `deployment` elemento en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación. El ejemplo se usa un `deploymentProvider` elemento para indicar la ubicación de actualización preferida.  
  
```xml  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)