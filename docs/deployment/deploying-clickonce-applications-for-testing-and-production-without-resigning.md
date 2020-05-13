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
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395321"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Implementar aplicaciones ClickOnce para servidores de prueba y producción sin renunciar
En este artículo se describe una característica de ClickOnce introducida en la versión 3.5 de .NET Framework que permite la implementación de aplicaciones ClickOnce desde varias ubicaciones de red sin volver a firmar o cambiar los manifiestos ClickOnce.

> [!NOTE]
> Renunciar sigue siendo el método preferido para implementar nuevas versiones de aplicaciones. Siempre que sea posible, utilice el método de renuncia. Para obtener más información, vea [ *Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Los desarrolladores de terceros y los ISV pueden optar por esta característica, lo que facilita a sus clientes la actualización de sus aplicaciones. Esta función se puede utilizar en las siguientes situaciones:

- Al actualizar una aplicación, no para la primera instalación de una aplicación.

- Cuando solo hay una configuración de la aplicación en un equipo. Por ejemplo, si una aplicación está configurada para apuntar a dos bases de datos diferentes, no puede utilizar esta característica.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Excluir deploymentProvider de los manifiestos de implementación
 En .NET Framework 2.0 y .NET Framework 3.0, cualquier aplicación ClickOnce que se `deploymentProvider` instala en el sistema para la disponibilidad sin conexión debe enumerar un en su manifiesto de implementación. A `deploymentProvider` menudo se conoce como la ubicación de actualización; es la ubicación donde ClickOnce busca actualizaciones de aplicaciones. Este requisito, junto con la necesidad de que los editores de aplicaciones firmarsus implementaciones, dificultaba que una empresa actualizara una aplicación ClickOnce de un proveedor u otro tercero. También hace que sea más difícil implementar la misma aplicación desde varias ubicaciones en la misma red.

 Con los cambios realizados en ClickOnce en .NET Framework 3.5, es posible que un tercero proporcione una aplicación ClickOnce a otra organización, que puede implementar la aplicación en su propia red.

 Para aprovechar esta característica, los desarrolladores de `deploymentProvider` aplicaciones ClickOnce deben excluir de sus manifiestos de implementación. Este requisito significa que `-providerUrl` debe excluir el argumento al crear manifiestos de implementación con Mage.exe. O bien, si va a generar manifiestos de implementación con MageUI.exe, debe asegurarse de que el cuadro de texto Ubicación de **inicio** de la ficha **Manifiesto** de aplicación se deja en blanco.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider y actualizaciones de aplicaciones
 A partir de .NET Framework 3.5, ya no es que tenga que especificar a `deploymentProvider` en el manifiesto de implementación para implementar una aplicación ClickOnce para el uso en línea y sin conexión. Este cambio admite el escenario en el que debe empaquetar y firmar la implementación usted mismo, pero permitir que otras empresas implementen la aplicación a través de sus redes.

 El punto importante a recordar es `deploymentProvider` que las aplicaciones que excluyen a no pueden `deploymentProvider` cambiar su ubicación de instalación durante las actualizaciones, hasta que envíen una actualización que incluya la etiqueta de nuevo.

 Aquí hay dos ejemplos para aclarar este punto. En el primer ejemplo, se publica una `deploymentProvider` aplicación ClickOnce que no `http://www.adatum.com/MyApplication/`tiene ninguna etiqueta y se pide a los usuarios que la instalen desde . Si decide que desea publicar la siguiente `http://subdomain.adatum.com/MyApplication/`actualización de la aplicación desde , no tiene forma `http://www.adatum.com/MyApplication/`de firmarlo en el manifiesto de implementación que reside en . Puede hacer una de dos cosas:

- Indique a los usuarios que desinstalen la versión anterior e instalen la nueva versión desde la nueva ubicación.

- Incluya una `http://www.adatum.com/MyApplication/` actualización que `deploymentProvider` incluya `http://www.adatum.com/MyApplication/`un punto a punto . A continuación, suelte `deploymentProvider` otra `http://subdomain.adatum.com/MyApplication/`actualización más adelante señalando a .

  En el segundo ejemplo, se publica una `deploymentProvider`aplicación ClickOnce que especifica y, a continuación, se decide quitarla. Una vez que `deploymentProvider` la nueva versión sin se descarga a los clientes, no `deploymentProvider` puede redirigir la ruta de acceso utilizada para las actualizaciones hasta que libere una versión de la aplicación que se ha restaurado. Al igual que `deploymentProvider` en el primer ejemplo, debe apuntar inicialmente a la ubicación de actualización actual, no a la nueva ubicación. En este caso, si intenta `deploymentProvider` insertar `http://subdomain.adatum.com/MyApplication/`un que hace referencia a , se produce un error en la siguiente actualización.

## <a name="create-a-deployment"></a>de una implementación
 Para obtener instrucciones paso a paso sobre la creación de implementaciones que se pueden implementar desde diferentes ubicaciones de red, vea [Tutorial: implementar manualmente una aplicación ClickOnce que no requiere volver a firmar y que conserva](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)la información de personalización de marca.

## <a name="see-also"></a>Vea también
- [*Mage.exe* (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Herramienta de generación y edición de manifiestos, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
