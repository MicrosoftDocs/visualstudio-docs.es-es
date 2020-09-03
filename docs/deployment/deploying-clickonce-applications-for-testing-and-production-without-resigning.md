---
title: Implementar aplicaciones ClickOnce sin volver a firmar
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89e1d7970b26d5ba9bd49090362a6a4e8c09f78d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395321"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Implementar aplicaciones ClickOnce para servidores de prueba y de producción sin tener que volver a firmar
En este artículo se describe una característica de ClickOnce introducida en la .NET Framework versión 3,5 que permite la implementación de aplicaciones ClickOnce desde varias ubicaciones de red sin tener que volver a firmar o cambiar los manifiestos de ClickOnce.

> [!NOTE]
> La nueva firma sigue siendo el método preferido para implementar nuevas versiones de aplicaciones. Siempre que sea posible, utilice el método de refirmación. Para obtener más información, vea [ *Mage.exe* (herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Los desarrolladores y ISV de terceros pueden participar en esta característica, lo que facilita a sus clientes la actualización de sus aplicaciones. Esta característica se puede usar en las siguientes situaciones:

- Al actualizar una aplicación, no a la primera instalación de una aplicación.

- Cuando solo hay una configuración de la aplicación en un equipo. Por ejemplo, si una aplicación está configurada para apuntar a dos bases de datos diferentes, no puede usar esta característica.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Excluir deploymentProvider de los manifiestos de implementación
 En el .NET Framework 2,0 y el .NET Framework 3,0, cualquier aplicación ClickOnce que se instale en el sistema para la disponibilidad sin conexión debe enumerar `deploymentProvider` en su manifiesto de implementación. A `deploymentProvider` menudo se conoce como la ubicación de actualización; es la ubicación donde ClickOnce comprueba las actualizaciones de la aplicación. Este requisito, junto con la necesidad de que los editores de aplicaciones firmen sus implementaciones, dificultaba a una empresa la actualización de una aplicación ClickOnce de un proveedor u otro tercero. También dificulta la implementación de la misma aplicación desde varias ubicaciones en la misma red.

 Con los cambios que se realizaron en ClickOnce en el .NET Framework 3,5, es posible que un tercero proporcione una aplicación ClickOnce a otra organización, lo que puede implementar la aplicación en su propia red.

 Para aprovechar esta característica, los desarrolladores de aplicaciones ClickOnce deben excluir `deploymentProvider` de sus manifiestos de implementación. Este requisito significa que debe excluir el `-providerUrl` argumento al crear los manifiestos de implementación con Mage.exe. O bien, si va a generar manifiestos de implementación con MageUI.exe, debe asegurarse de que el cuadro de texto **Ubicación de inicio** de la pestaña **manifiesto de aplicación** se deja en blanco.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider y actualizaciones de aplicaciones
 A partir del .NET Framework 3,5, ya no es necesario especificar un `deploymentProvider` en el manifiesto de implementación para implementar una aplicación ClickOnce para uso en línea y sin conexión. Este cambio admite el escenario en el que es necesario empaquetar y firmar la implementación usted mismo, pero permitir que otras empresas implementen la aplicación a través de sus redes.

 Lo importante es recordar que las aplicaciones que excluyan un `deploymentProvider` no pueden cambiar su ubicación de instalación durante las actualizaciones, hasta que envíen una actualización que incluya la `deploymentProvider` etiqueta de nuevo.

 A continuación se muestran dos ejemplos para aclarar este punto. En el primer ejemplo, se publica una aplicación ClickOnce que no tiene `deploymentProvider` etiqueta y se pide a los usuarios que la instalen desde `http://www.adatum.com/MyApplication/` . Si decide que desea publicar la siguiente actualización de la aplicación de `http://subdomain.adatum.com/MyApplication/` , no tiene forma de hacerlo en el manifiesto de implementación que reside en `http://www.adatum.com/MyApplication/` . Puede realizar una de estas dos acciones:

- Indique a los usuarios que desinstalen la versión anterior e instale la nueva versión desde la nueva ubicación.

- Incluya una actualización de `http://www.adatum.com/MyApplication/` que incluya un que `deploymentProvider` apunte a `http://www.adatum.com/MyApplication/` . A continuación, libere otra actualización más adelante con `deploymentProvider` apuntando a `http://subdomain.adatum.com/MyApplication/` .

  En el segundo ejemplo, se publica una aplicación ClickOnce que especifica y, `deploymentProvider` a continuación, se decide quitarla. Una vez que la nueva versión sin `deploymentProvider` se descarga en los clientes, no se puede redirigir la ruta de acceso que se usa para las actualizaciones hasta que se publica una versión de la aplicación que se ha `deploymentProvider` restaurado. Como en el primer ejemplo, `deploymentProvider` debe apuntar inicialmente a la ubicación de actualización actual, no a la nueva ubicación. En este caso, si intenta insertar un `deploymentProvider` que hace referencia a `http://subdomain.adatum.com/MyApplication/` , se produce un error en la siguiente actualización.

## <a name="create-a-deployment"></a>de una implementación
 Para obtener instrucciones paso a paso sobre cómo crear implementaciones que se pueden implementar desde diferentes ubicaciones de red, vea [Tutorial: implementar manualmente una aplicación ClickOnce que no requiera volver a firmar y que conserve la información de personalización de marca](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

## <a name="see-also"></a>Vea también
- [*Mage.exe* (herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (herramienta de generación y edición de manifiestos, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
