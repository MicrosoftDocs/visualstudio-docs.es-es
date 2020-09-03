---
title: Implementación de aplicaciones ClickOnce para servidores de prueba y producción sin tener que volver a firmar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8e41e67d5e2800acc41e1220fe632001420a274
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395370"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Implementar aplicaciones ClickOnce para los servidores de pruebas y producción sin nueva firma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describe una nueva característica de ClickOnce introducida en la .NET Framework versión 3,5 que permite la implementación de aplicaciones ClickOnce desde varias ubicaciones de red sin tener que volver a firmar o cambiar los manifiestos de ClickOnce.  
  
> [!NOTE]
> La nueva firma sigue siendo el método preferido para implementar nuevas versiones de aplicaciones. Siempre que sea posible, utilice el método de refirmación. Para más información, consulte [Mage.exe (Herramienta de generación y edición de manifiestos)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Los desarrolladores y ISV de terceros pueden participar en esta característica, lo que facilita a sus clientes la actualización de sus aplicaciones. Esta característica se puede usar en las siguientes situaciones:  
  
- Al actualizar una aplicación, no la primera instalación de una aplicación.  
  
- Cuando solo hay una configuración de la aplicación en un equipo. Por ejemplo, si una aplicación está configurada para apuntar a dos bases de datos diferentes, no puede usar esta característica.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Exclusión de deploymentProvider de manifiestos de implementación  
 En el .NET Framework 2,0 y el .NET Framework 3,0, cualquier aplicación ClickOnce que se instale en el sistema para la disponibilidad sin conexión debe especificar un `deploymentProvider` en su manifiesto de implementación. A `deploymentProvider` menudo se conoce como la ubicación de actualización; es la ubicación en la que ClickOnce comprobará las actualizaciones de la aplicación. Este requisito, junto con la necesidad de que los publicadores de aplicaciones firmen sus implementaciones, dificultaba a una empresa la actualización de una aplicación ClickOnce de un proveedor u otro tercero. También dificulta la implementación de la misma aplicación desde varias ubicaciones en la misma red.  
  
 Con los cambios que se realizaron en ClickOnce en el .NET Framework 3,5, es posible que un tercero proporcione una aplicación ClickOnce a otra organización, lo que puede implementar la aplicación en su propia red.  
  
 Para aprovechar esta característica, los desarrolladores de aplicaciones ClickOnce deben excluir `deploymentProvider` de sus manifiestos de implementación. Esto significa que se excluye el `-providerUrl` argumento cuando se crean manifiestos de implementación con Mage.exe, o se garantiza que el cuadro de texto **Ubicación de inicio** de la pestaña **manifiesto de aplicación** se deja en blanco si se generan manifiestos de implementación con MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider y actualizaciones de aplicaciones  
 A partir del .NET Framework 3,5, ya no es necesario especificar un `deploymentProvider` en el manifiesto de implementación para implementar una aplicación ClickOnce para uso en línea y sin conexión. Esto es compatible con el escenario en el que es necesario empaquetar y firmar la implementación usted mismo, pero permitir que otras empresas implementen la aplicación en sus redes.  
  
 El punto clave que hay que recordar es que las aplicaciones que excluyan un `deploymentProvider` no pueden cambiar su ubicación de instalación durante las actualizaciones, hasta que envíen una actualización que incluya la `deploymentProvider` etiqueta de nuevo.  
  
 A continuación se muestran dos ejemplos para aclarar este punto. En el primer ejemplo, se publica una aplicación ClickOnce que no tiene `deploymentProvider` etiqueta y se pide a los usuarios que la instalen desde `http://www.adatum.com/MyApplication/` . Si decide que desea publicar la siguiente actualización de la aplicación desde `http://subdomain.adatum.com/MyApplication/` , no tendrá forma de indicar Esto en el manifiesto de implementación que reside en `http://www.adatum.com/MyApplication/` . Puede realizar una de estas dos acciones:  
  
- Indique a los usuarios que desinstalen la versión anterior e instale la nueva versión desde la nueva ubicación.  
  
- Incluya una actualización de `http://www.adatum.com/MyApplication/` que incluya un que `deploymentProvider` apunte a `http://www.adatum.com/MyApplication/` . A continuación, libere otra actualización más adelante con `deploymentProvider` apuntando a `http://subdomain.adatum.com/MyApplication/` .  
  
  En el segundo ejemplo, se publica una aplicación ClickOnce que especifica y, `deploymentProvider` a continuación, se decide quitarla. Una vez que la nueva versión sin se haya `deploymentProvider` descargado en los clientes, no podrá redirigir la ruta de acceso que se usa para las actualizaciones hasta que publique una versión de la aplicación que se haya `deploymentProvider` restaurado. Como en el primer ejemplo, `deploymentProvider` debe apuntar inicialmente a la ubicación de actualización actual, no a la nueva ubicación. En este caso, si intenta insertar un `deploymentProvider` que hace referencia a `http://subdomain.adatum.com/MyApplication/` , se producirá un error en la siguiente actualización.  
  
## <a name="creating-a-deployment"></a>Creación de una implementación  
 Para obtener instrucciones paso a paso sobre la creación de implementaciones que se pueden implementar desde diferentes ubicaciones de red, vea [Tutorial: implementar manualmente una aplicación ClickOnce que no requiera volver a firmar y que conserve la información de personalización de marca](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
## <a name="see-also"></a>Consulte también  
 [Mage.exe (Herramienta de generación y edición de manifiestos)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Herramienta de generación y edición de manifiestos, cliente gráfico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
