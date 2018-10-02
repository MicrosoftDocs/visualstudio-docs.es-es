---
title: Implementar aplicaciones ClickOnce para las pruebas y los servidores de producción sin nueva firma | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 384292be2f08eef453dba5623783ef8865107d54
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581442"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Implementar aplicaciones ClickOnce para los servidores de pruebas y producción sin nueva firma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [implementación ClickOnce aplicaciones para las pruebas y los servidores de producción sin Resigning](https://docs.microsoft.com/visualstudio/deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning).  
  
En este tema se describe una nueva característica de introducidas en .NET Framework versión 3.5 que permite la implementación de aplicaciones ClickOnce desde varias ubicaciones de red sin volver a firmar ni cambiar la ClickOnce manifiestos de ClickOnce.  
  
> [!NOTE]
>  Nueva firma sigue siendo el método preferido para implementar nuevas versiones de las aplicaciones. Siempre que sea posible, utilice el método volver a firmar. Para más información, consulte [Mage.exe (Herramienta de generación y edición de manifiestos)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Los desarrolladores de terceros y los ISV pueden participar en esta característica, facilitando la tarea para sus clientes actualizar sus aplicaciones. Esta característica puede usarse en las situaciones siguientes:  
  
-   Al actualizar una aplicación, no en la primera instalación de una aplicación.  
  
-   Cuando hay solo una configuración de la aplicación en un equipo. Por ejemplo, si una aplicación está configurada para que apunte a dos bases de datos, no puede usar esta característica.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Exclusión de deploymentProvider de manifiestos de implementación  
 En .NET Framework 2.0 y .NET Framework 3.0, deben especificar las aplicaciones ClickOnce que se instalación en el sistema para la disponibilidad sin conexión un `deploymentProvider` en su manifiesto de implementación. El `deploymentProvider` a menudo se conoce como la ubicación de actualización es la ubicación en la que se comprobará ClickOnce actualizaciones de la aplicación. Este requisito, junto con la necesidad de los editores de aplicaciones firmar sus implementaciones, era difícil para una empresa actualizar una aplicación ClickOnce de un proveedor u otras aplicaciones de terceros. También resulta más difícil de implementar la misma aplicación desde varias ubicaciones en la misma red.  
  
 Con los cambios que se realizaron en ClickOnce en .NET Framework 3.5, es posible que un tercero para proporcionar una aplicación ClickOnce en otra organización, que, a continuación, puede implementar la aplicación en su propia red.  
  
 Con el fin de aprovechar las ventajas de esta característica, deben excluir a los desarrolladores de aplicaciones ClickOnce `deploymentProvider` desde su implementación de manifiestos. Esto significa que excluir el `-providerUrl` manifiestos de argumento cuando se crea la implementación con Mage.exe o asegurándose de que el **iniciar ubicación** cuadro de texto en el **el manifiesto de aplicación** ficha se deja en blanco si se va a generar los manifiestos de implementación con MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider y actualizaciones de aplicaciones  
 A partir de .NET Framework 3.5, ya no tiene que especificar un `deploymentProvider` en el manifiesto de implementación para implementar una aplicación ClickOnce para uso en línea y sin conexión. Esto es compatible con el escenario donde tiene que empaquetar y firmar la implementación por sí mismo, pero permitir que otras empresas implementar la aplicación a través de sus redes.  
  
 El punto clave que recordar es que las aplicaciones que excluirán un `deploymentProvider` no se puede cambiar su ubicación de instalación durante las actualizaciones, hasta que se incluyen una actualización que incluye la `deploymentProvider` etiqueta de nuevo.  
  
 Estos son dos ejemplos para aclarar este punto. En el primer ejemplo, publica una aplicación ClickOnce que no tiene ningún `deploymentProvider` etiqueta y pedir a los usuarios instalen desde http://www.adatum.com/MyApplication/. Si decide que desea publicar la próxima actualización de la aplicación de http://subdomain.adatum.com/MyApplication/, no habrá forma de lo que significa esto en el manifiesto de implementación que se encuentra en http://www.adatum.com/MyApplication/. Puede hacer dos cosas:  
  
-   Indique a los usuarios para desinstalar la versión anterior e instalar la nueva versión desde la nueva ubicación.  
  
-   Incluir una actualización en http://www.adatum.com/MyApplication/ que incluye un `deploymentProvider` señalando a http://www.adatum.com/MyApplication/. A continuación, suelte otra actualización posterior con `deploymentProvider` señalando a http://subdomain.adatum.com/MyApplication/.  
  
 En el segundo ejemplo, publica una aplicación ClickOnce que especifica `deploymentProvider`, y, a continuación, decide quitarlo. Una vez que la nueva versión sin `deploymentProvider` se ha descargado a los clientes, no podrá redirigir la ruta de acceso que se usan para las actualizaciones hasta que se publique una versión de la aplicación que tiene `deploymentProvider` restaurado. Al igual que con el primer ejemplo, `deploymentProvider` debe señalar inicialmente a la ubicación de actualización actual, no su nueva ubicación. En este caso, si se intenta insertar un `deploymentProvider` que hace referencia a http://subdomain.adatum.com/MyApplication/, se producirá un error en la siguiente actualización.  
  
## <a name="creating-a-deployment"></a>Creación de una implementación  
 Para obtener instrucciones paso a paso sobre la creación de implementaciones que se pueden implementar desde distintas ubicaciones de red, consulte [Tutorial: implementar manualmente una aplicación ClickOnce que Does no requerir nueva firma y esa información de personalización de marca conserva](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## <a name="see-also"></a>Vea también  
 [Mage.exe (Herramienta de generación y edición de manifiestos)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Herramienta de generación y edición de manifiestos, cliente gráfico)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)



