---
title: Implementar aplicaciones ClickOnce para las pruebas y los servidores de producción sin nueva firma | Microsoft Docs
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
ms.openlocfilehash: d573de9889d286a7b634890e0d8b469541bc741f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407050"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Implementar aplicaciones ClickOnce para los servidores de pruebas y producción sin nueva firma
En este artículo se describe una característica de introducidas en .NET Framework versión 3.5 que permite la implementación de aplicaciones ClickOnce desde varias ubicaciones de red sin volver a firmar ni cambiar la ClickOnce manifiestos de ClickOnce.

> [!NOTE]
> Nueva firma sigue siendo el método preferido para implementar nuevas versiones de las aplicaciones. Siempre que sea posible, utilice el método volver a firmar. Para más información, consulte [*Mage.exe* (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Los desarrolladores de terceros y los ISV pueden participar en esta característica, facilitando la tarea para sus clientes actualizar sus aplicaciones. Esta característica puede usarse en las situaciones siguientes:

- Al actualizar una aplicación, no en la primera instalación de una aplicación.

- Cuando hay solo una configuración de la aplicación en un equipo. Por ejemplo, si una aplicación está configurada para que apunte a dos bases de datos, no puede usar esta característica.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Excluir deploymentProvider de manifiestos de implementación
 En .NET Framework 2.0 y .NET Framework 3.0, deben enumerar las aplicaciones ClickOnce que se instalación en el sistema para la disponibilidad sin conexión un `deploymentProvider` en su manifiesto de implementación. El `deploymentProvider` a menudo se conoce como la ubicación de actualización es la ubicación donde ClickOnce busca actualizaciones de la aplicación. Este requisito, junto con la necesidad de los editores de aplicaciones firmar sus implementaciones, era difícil para una empresa actualizar una aplicación ClickOnce de un proveedor u otras aplicaciones de terceros. También resulta más difícil de implementar la misma aplicación desde varias ubicaciones en la misma red.

 Con los cambios que se realizaron en ClickOnce en .NET Framework 3.5, es posible que un tercero para proporcionar una aplicación ClickOnce en otra organización, que, a continuación, puede implementar la aplicación en su propia red.

 Con el fin de aprovechar las ventajas de esta característica, deben excluir a los desarrolladores de aplicaciones ClickOnce `deploymentProvider` desde su implementación de manifiestos. Este requisito significa que debe excluir el `-providerUrl` manifiestos de argumento cuando se crea la implementación con Mage.exe. O bien, si va a generar los manifiestos de implementación con MageUI.exe, primero debe asegurarse que la **iniciar ubicación** cuadro de texto en el **Application Manifest** ficha se deja en blanco.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider y aplicación de actualizaciones
 A partir de .NET Framework 3.5, ya no tiene que especificar un `deploymentProvider` en el manifiesto de implementación para implementar una aplicación ClickOnce para uso en línea y sin conexión. Este cambio admite el escenario donde tiene que empaquetar y firmar la implementación por sí mismo, pero permitir que otras empresas implementar la aplicación a través de sus redes.

 Es importante que recuerde que las aplicaciones que excluirán un `deploymentProvider` no se puede cambiar su ubicación de instalación durante las actualizaciones, hasta que se incluyen una actualización que incluye la `deploymentProvider` etiqueta de nuevo.

 Estos son dos ejemplos para aclarar este punto. En el primer ejemplo, publica una aplicación ClickOnce que no tiene ningún `deploymentProvider` etiqueta y pedir a los usuarios instalen desde http://www.adatum.com/MyApplication/. Si decide que desea publicar la próxima actualización de la aplicación de http://subdomain.adatum.com/MyApplication/, no hay forma de lo que significa esto en el manifiesto de implementación que se encuentra en http://www.adatum.com/MyApplication/. Puede hacer dos cosas:

- Indique a los usuarios para desinstalar la versión anterior e instalar la nueva versión desde la nueva ubicación.

- Incluir una actualización en http://www.adatum.com/MyApplication/ que incluye un `deploymentProvider` señalando a http://www.adatum.com/MyApplication/. A continuación, suelte otra actualización posterior con `deploymentProvider` señalando a http://subdomain.adatum.com/MyApplication/.

  En el segundo ejemplo, publica una aplicación ClickOnce que especifica `deploymentProvider`, y, a continuación, decide quitarlo. Una vez que la nueva versión sin `deploymentProvider` se descarga a los clientes, no se puede redirigir la ruta de acceso que se usan para las actualizaciones hasta que se publique una versión de la aplicación que tiene `deploymentProvider` restaurado. Al igual que con el primer ejemplo, `deploymentProvider` debe señalar inicialmente a la ubicación de actualización actual, no su nueva ubicación. En este caso, si se intenta insertar un `deploymentProvider` que hace referencia a http://subdomain.adatum.com/MyApplication/, a continuación, se produce un error en la siguiente actualización.

## <a name="create-a-deployment"></a>Creación de una implementación
 Para obtener instrucciones paso a paso sobre la creación de implementaciones que se pueden implementar desde distintas ubicaciones de red, consulte [Tutorial: Implementar manualmente una aplicación ClickOnce que no requiere volver a firmar y que conserve la información de personalización de marca](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

## <a name="see-also"></a>Vea también
- [*Mage.exe* (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Herramienta de generación y edición de manifiestos, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)