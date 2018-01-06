---
title: "Implementar aplicaciones ClickOnce para las pruebas y los servidores de producción sin nueva firma | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: ec7265f91d5c202d5885b7f1994aa6f037d6d2ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Implementar aplicaciones ClickOnce para los servidores de pruebas y producción sin nueva firma
Este tema describe una nueva característica de ClickOnce introducida en .NET Framework versión 3.5 que permite la implementación de aplicaciones ClickOnce desde varias ubicaciones de red sin volver a firmar ni cambiar la ClickOnce manifiestos.  
  
> [!NOTE]
>  Volver a firmar sigue siendo el método preferido para implementar nuevas versiones de las aplicaciones. Siempre que sea posible, utilice el método volver a firmar. Para más información, consulte [Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Los desarrolladores de aplicaciones de terceros y los ISV pueden participar en esta característica, facilitando a sus clientes actualizar sus aplicaciones. Esta característica se puede utilizar en las situaciones siguientes:  
  
-   Al actualizar una aplicación, no en la primera instalación de una aplicación.  
  
-   Cuando hay una sola configuración de la aplicación en un equipo. Por ejemplo, si una aplicación está configurada para que apunte a dos bases de datos diferentes, no puede usar esta característica.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Exclusión de deploymentProvider de manifiestos de implementación  
 En .NET Framework 2.0 y .NET Framework 3.0, deben especificar las aplicaciones ClickOnce que se instalación en el sistema para disponibilidad sin conexión un `deploymentProvider` en su manifiesto de implementación. El `deploymentProvider` a menudo se conoce como la ubicación de actualización; es la ubicación en la que ClickOnce comprobará las actualizaciones de la aplicación. Este requisito, junto con la necesidad de los editores de aplicaciones firmen sus implementaciones, dificultaba a una empresa para actualizar una aplicación ClickOnce desde un proveedor u otro tercero. También resulta más difícil de implementar la misma aplicación de varias ubicaciones en la misma red.  
  
 Con los cambios que se realizaron en ClickOnce en .NET Framework 3.5, es posible que un tercero proporcionar una aplicación ClickOnce en otra organización, que, a continuación, se puede implementar la aplicación en su propia red.  
  
 Con el fin de sacar partido de esta característica, deben excluir los desarrolladores de aplicaciones ClickOnce `deploymentProvider` de su implementación de manifiestos. Esto significa sin incluir el `-providerUrl` manifiestos de argumento cuando se crea la implementación con Mage.exe o asegurándose de que el **iniciar ubicación** cuadro de texto en el **Application Manifest** ficha se deja en blanco si se va a generar los manifiestos de implementación con MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider y actualizaciones de aplicaciones  
 A partir de .NET Framework 3.5, ya no tiene que especificar un `deploymentProvider` en el manifiesto de implementación para implementar una aplicación ClickOnce para el uso en línea y sin conexión. Esto es compatible con el escenario donde debe empaquetar y firmar la implementación personalmente, pero permitir que otras empresas implementar la aplicación a través de sus redes.  
  
 El punto clave que recordar es que las aplicaciones que excluirán una `deploymentProvider` no se puede cambiar su ubicación de instalación durante las actualizaciones, hasta que se incluyen una actualización que incluye la `deploymentProvider` etiqueta de nuevo.  
  
 Éstos son dos ejemplos para aclarar este concepto. En el primer ejemplo, publicar una aplicación ClickOnce que no tiene ningún `deploymentProvider` etiqueta y se pregunte a los usuarios lo instalen desde http://www.adatum.com/MyApplication/. Si decide que desea publicar la próxima actualización de la aplicación en http://subdomain.adatum.com/MyApplication/, no tendrá ninguna manera de indicarlo en el manifiesto de implementación que se encuentra en http://www.adatum.com/MyApplication/. Puede realizar una de estas dos cosas:  
  
-   Indique a los usuarios para desinstalar la versión anterior e instalar la nueva versión desde la nueva ubicación.  
  
-   Incluir una actualización en http://www.adatum.com/MyApplication/ que contenga un `deploymentProvider` señale a http://www.adatum.com/MyApplication/. A continuación, suelte otra actualización posterior con `deploymentProvider` que apunta a http://subdomain.adatum.com/MyApplication/.  
  
 En el segundo ejemplo, publicar una aplicación ClickOnce que especifica `deploymentProvider`, y, a continuación, decide quitarlo. Una vez la nueva versión sin `deploymentProvider` se ha descargado a los clientes, no podrá redirigir la ruta de acceso que se usan para las actualizaciones hasta que se publica una versión de la aplicación que tiene `deploymentProvider` restaurado. Al igual que con el primer ejemplo, `deploymentProvider` inicialmente debe apuntar a la ubicación de actualización actual, no la nueva ubicación. En este caso, si se intenta insertar un `deploymentProvider` que hace referencia a http://subdomain.adatum.com/MyApplication/, a continuación, se producirá un error en la siguiente actualización.  
  
## <a name="creating-a-deployment"></a>Creación de una implementación  
 Para obtener instrucciones paso a paso sobre cómo crear implementaciones que se pueden implementar desde distintas ubicaciones de red, consulte [Tutorial: implementar manualmente una aplicación ClickOnce que Does no requieren nueva firma y esa información de personalización de marca conserva](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## <a name="see-also"></a>Vea también  
 [Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Herramienta de generación y edición de manifiestos, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)