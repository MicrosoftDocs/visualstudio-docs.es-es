---
title: '&lt;implementación&gt; elemento (implementación ClickOnce) | Microsoft Docs'
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
ms.openlocfilehash: 5a7a22e683f1db05544f235308dc5ba495f74095
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629526"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;implementación&gt; elemento (implementación ClickOnce)
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
 El elemento `deployment` es obligatorio y se encuentra en el espacio de nombres `urn:schemas-microsoft-com:asm.v1` . El elemento tiene los atributos siguientes.


| Atributo | Descripción |
|--------------------------| - |
| `install` | Obligatorio. Especifica si esta aplicación define una presencia en el Windows **iniciar** menú y, en el Panel de Control **agregar o quitar programas** aplicación. Los valores válidos son `true` y `false`. Si `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] siempre se ejecutará la versión más reciente de esta aplicación desde la red y no reconocerá el `subscription` elemento. |
| `minimumRequiredVersion` | Opcional. Especifica la versión mínima de la aplicación que se puede ejecutar en el cliente. Si el número de versión de la aplicación es menor que el número de versión proporcionado en el manifiesto de implementación, no se ejecutará la aplicación. Números de versión deben especificarse en el formato `N.N.N.N`, donde `N` es un entero sin signo. Si el `install` atributo es `false`, `minimumRequiredVersion` no debe establecerse. |
| `mapFileExtensions` | Opcional. Tiene como valor predeterminado `false`. Si `true`, todos los archivos de la implementación deben tener una extensión. deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eliminará esta extensión de estos archivos, en cuanto descarga desde el servidor Web. Si publica la aplicación mediante el uso de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], esta extensión se agregará automáticamente a todos los archivos. Este parámetro permite que todos los archivos dentro de un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación se descarguen desde un servidor Web que bloquea la transmisión de archivos que terminan en "unsafe" extensiones como .exe. |
| `disallowUrlActivation` | Opcional. Tiene como valor predeterminado `false`. Si `true`, impide que una aplicación instalada desde la que se inicia al hacer clic en la dirección URL o escribiendo la dirección URL en Internet Explorer. Si el `install` atributo no está presente, se omite este atributo. |
| `trustURLParameters` | Opcional. Tiene como valor predeterminado `false`. Si `true`, permite que la dirección URL para que contenga los parámetros de cadena de consulta que se pasan a la aplicación, tanto como argumentos de línea de comandos se pasan a una aplicación de línea de comandos. Para obtener más información, consulte [Cómo: recuperar información de cadena de consulta en una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Si el `disallowUrlActivation` atributo es `true`, `trustUrlParameters` debe ser excluidos del manifiesto o establecida explícitamente en `false`. |

 El `deployment` elemento también contiene los siguientes elementos secundarios.

## <a name="subscription"></a>subscription
 Opcional. Contiene el `update` elemento. El elemento `subscription` no tiene atributos. Si el `subscription` elemento no existe, el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación no buscará actualizaciones. Si el `install` atributo de la `deployment` es elemento `false`, el `subscription` se omite el elemento, porque un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación que se inicia desde la red siempre utiliza la versión más reciente.

## <a name="update"></a>actualizar
 Obligatorio. Este es un elemento secundario de la `subscription` elemento y contiene el `beforeApplicationStartup` o `expiration` elemento. `beforeApplicationStartup` y `expiration` no se especifican en el mismo manifiesto de implementación.

 El elemento `update` no tiene atributos.

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 Opcional. Este es un elemento secundario de la `update` elemento y no tiene atributos. Cuando el `beforeApplicationStartup` elemento existe, la aplicación estará bloqueado cuando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] busca actualizaciones, si el cliente está en línea. Si este elemento no existe, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] primero buscará actualizaciones en función de los valores especificados para el `expiration` elemento. `beforeApplicationStartup` y `expiration` no se especifican en el mismo manifiesto de implementación.

## <a name="expiration"></a>expiración
 Opcional. Este es un elemento secundario de la `update` elemento, y no tiene elementos secundarios. `beforeApplicationStartup` y `expiration` no se especifican en el mismo manifiesto de implementación. Cuando se produce la comprobación de actualización y se detecta una versión actualizada, la nueva versión almacena en caché mientras se ejecuta la versión existente. La nueva versión, a continuación, se instala en el siguiente inicio de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.

 El `expiration` elemento admite los siguientes atributos.

|Atributo|Descripción|
|---------------|-----------------|
|`maximumAge`|Obligatorio. Identifica la antigüedad debe ser la actualización actual antes de que la aplicación realice una comprobación de actualizaciones. La unidad de tiempo viene determinada por la `unit` atributo.|
|`unit`|Obligatorio. Identifica la unidad de tiempo para `maximumAge`. Las unidades válidas son `hours`, `days`, y `weeks`.|

## <a name="deploymentprovider"></a>deploymentProvider
 Para .NET Framework 2.0, este elemento es necesario si el manifiesto de implementación contiene un `subscription` sección. Para .NET Framework 3.5 y versiones posteriores, este elemento es opcional y se usará de forma predeterminada el servidor y la ruta de acceso de archivo en el que se ha detectado el manifiesto de implementación.

 Este elemento es un elemento secundario del elemento `deployment` y tiene el siguiente atributo.


| Atributo | Descripción |
|------------| - |
| `codebase` | Obligatorio. Identifica la ubicación, como un identificador uniforme de recursos (URI), del manifiesto de implementación que se usa para actualizar el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Este elemento también permite reenviar las ubicaciones de actualización para las instalaciones basadas en CD. Debe ser un URI válido. |

## <a name="remarks"></a>Comentarios
 Puede configurar su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación para buscar actualizaciones durante el inicio, busque actualizaciones después del inicio, o no buscar nunca actualizaciones. Para buscar actualizaciones en el inicio, asegúrese de que el `beforeApplicationStartup` elemento existe en el `update` elemento. Para buscar actualizaciones después del inicio, asegúrese de que el `expiration` elemento existe en el `update` elemento y que se proporcionan los intervalos de actualización.

 Para deshabilitar la comprobación de actualizaciones, quite el `subscription` elemento. Cuando se especifica en el manifiesto de implementación para no buscar nunca actualizaciones, puede comprobar manualmente las actualizaciones mediante el uso de la <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> método.

 Para obtener más información sobre cómo deploymentProvider se relaciona con las actualizaciones, consulte [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="examples"></a>Ejemplos
 En el ejemplo de código siguiente se ilustra un `deployment` elemento en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación. El ejemplo se usa un `deploymentProvider` elemento para indicar la ubicación de actualización preferida.

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