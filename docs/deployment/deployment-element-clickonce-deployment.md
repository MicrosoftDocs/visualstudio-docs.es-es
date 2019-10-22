---
title: '&lt;Deployment&gt; (elemento, implementación ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 988ce0859ab24377395cc4077f9e6fa42e0487a5
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887857"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;Deployment&gt; (elemento, implementación de ClickOnce)
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
 El elemento `deployment` es obligatorio y se encuentra en el espacio de nombres `urn:schemas-microsoft-com:asm.v2` . El elemento tiene los atributos siguientes.

| Atributo | DESCRIPCIÓN |
|--------------------------| - |
| `install` | Necesario. Especifica si esta aplicación define una presencia en el menú **Inicio** de Windows y en la aplicación **Agregar o quitar programas** del panel de control. Los valores válidos son `true` y `false`. Si `false` `subscription` , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] siempre ejecutará la versión más reciente de esta aplicación desde la red y no reconocerá el elemento. |
| `minimumRequiredVersion` | Opcional. Especifica la versión mínima de esta aplicación que se puede ejecutar en el cliente. Si el número de versión de la aplicación es menor que el número de versión proporcionado en el manifiesto de implementación, la aplicación no se ejecutará. Los números de versión se deben especificar con `N.N.N.N`el formato `N` , donde es un entero sin signo. Si el `install` atributo es `false`, `minimumRequiredVersion` no se debe establecer. |
| `mapFileExtensions` | Opcional. Tiene como valor predeterminado `false`. Si `true`es, todos los archivos de la implementación deben tener una extensión. deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]quitará esta extensión de estos archivos tan pronto como los Descargue del servidor Web. Si publica la aplicación [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]mediante, agrega automáticamente esta extensión a todos los archivos. Este parámetro permite que se descarguen todos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] los archivos de una implementación desde un servidor Web que bloquea la transmisión de archivos que terminan en extensiones "no seguras" como. exe. |
| `disallowUrlActivation` | Opcional. Tiene como valor predeterminado `false`. Si `true`, impide que se inicie una aplicación instalada haciendo clic en la dirección URL o escribiendo la dirección URL en Internet Explorer. Si el `install` atributo no está presente, se omite este atributo. |
| `trustURLParameters` | Opcional. Tiene como valor predeterminado `false`. Si `true`es, permite que la dirección URL contenga los parámetros de cadena de consulta que se pasan a la aplicación, de forma muy similar a como se pasan los argumentos de línea de comandos a una aplicación de línea de comandos. Para obtener más información, vea [Cómo: Recuperación de información de la cadena de consulta de una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Si el `disallowUrlActivation` atributo es `true`, `trustUrlParameters` se debe excluir del manifiesto o establecerse explícitamente en `false`. |

 El `deployment` elemento también contiene los siguientes elementos secundarios.

## <a name="subscription"></a>subscription
 Opcional. Contiene el `update` elemento. El elemento `subscription` no tiene atributos. Si el `subscription` elemento no existe, la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación nunca buscará actualizaciones. Si el `install` `deployment` atributo del elemento es `false`, se omite `subscription` el elemento, porque una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación que se inicia desde la red siempre usa la versión más reciente.

## <a name="update"></a>actualizar
 Necesario. Este elemento es un elemento secundario del `subscription` elemento y contiene el `beforeApplicationStartup` `expiration` elemento o. `beforeApplicationStartup`y `expiration` no se pueden especificar en el mismo manifiesto de implementación.

 El elemento `update` no tiene atributos.

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 Opcional. Este elemento es un elemento secundario del `update` elemento y no tiene atributos. Cuando el `beforeApplicationStartup` elemento existe, la aplicación se bloqueará al [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] comprobar si hay actualizaciones, si el cliente está en línea. Si este elemento no existe, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] buscará primero las actualizaciones en función de los valores especificados para el `expiration` elemento. `beforeApplicationStartup`y `expiration` no se pueden especificar en el mismo manifiesto de implementación.

## <a name="expiration"></a>expiración
 Opcional. Este elemento es un elemento secundario del `update` elemento y no tiene elementos secundarios. `beforeApplicationStartup`y `expiration` no se pueden especificar en el mismo manifiesto de implementación. Cuando se realiza la comprobación de la actualización y se detecta una versión actualizada, la nueva versión se almacena en caché mientras se ejecuta la versión existente. A continuación, la nueva versión se instala en el siguiente inicio [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de la aplicación.

 El `expiration` elemento admite los siguientes atributos.

|Atributo|DESCRIPCIÓN|
|---------------|-----------------|
|`maximumAge`|Necesario. Identifica la antigüedad de la actualización actual antes de que la aplicación realice una comprobación de actualización. El `unit` atributo determina la unidad de tiempo.|
|`unit`|Necesario. Identifica la unidad de tiempo para `maximumAge`. Las unidades válidas `days`son `hours`, `weeks`y.|

## <a name="deploymentprovider"></a>deploymentProvider
 En el .NET Framework 2,0, este elemento es necesario si el manifiesto de implementación contiene `subscription` una sección. En el .NET Framework 3,5 y versiones posteriores, este elemento es opcional y tomará como valor predeterminado el servidor y la ruta de acceso del archivo en el que se detectó el manifiesto de implementación.

 Este elemento es un elemento secundario del elemento `deployment` y tiene el siguiente atributo.

| Atributo | DESCRIPCIÓN |
|------------| - |
| `codebase` | Necesario. Identifica la ubicación, como un identificador uniforme de recursos (URI), del manifiesto de implementación que se utiliza para actualizar la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Este elemento también permite el reenvío de ubicaciones de actualización para instalaciones basadas en CD. Debe ser un URI válido. |

## <a name="remarks"></a>Comentarios
 Puede configurar la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para que busque actualizaciones en el inicio, busque actualizaciones después del inicio o no compruebe nunca si hay actualizaciones. Para buscar actualizaciones en el inicio, asegúrese de que `beforeApplicationStartup` el elemento existe en `update` el elemento. Para buscar actualizaciones después del inicio, asegúrese de que `expiration` el elemento existe en `update` el elemento y que se proporcionan intervalos de actualización.

 Para deshabilitar la comprobación de actualizaciones, `subscription` Quite el elemento. Cuando se especifica en el manifiesto de implementación para no buscar nunca actualizaciones, todavía puede comprobar manualmente si hay actualizaciones mediante el <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> método.

 Para obtener más información sobre cómo se relaciona deploymentProvider con las actualizaciones, vea [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="examples"></a>Ejemplos
 En el ejemplo de código siguiente se `deployment` muestra un elemento [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en un manifiesto de implementación. En el ejemplo se `deploymentProvider` usa un elemento para indicar la ubicación de actualización preferida.

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
- [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)