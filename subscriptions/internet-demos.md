---
title: Demostraciones en Internet a través de Terminal Services en suscripciones de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 1c5ede60-cb5a-4d5f-a6a2-a1f536f6c4ad
ms.date: 03/21/2021
ms.topic: conceptual
description: Aprenda a usar claves de producto para admitir demostraciones en Internet a través de Terminal Services y habilitar el acceso a RDS
ms.openlocfilehash: c074dfe12ed7c1fea5ad60f7e0c8019e133a6d1b
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776550"
---
# <a name="internet-demonstrations-via-terminal-services"></a>Demostraciones en Internet a través de Terminal Services
Con una suscripción de Visual Studio, podrá brindar a los usuarios finales acceso a demostraciones de sus programas en Internet a través de Terminal Services (Windows Server 2003 o Windows Server 2008) o Servicios de Escritorio remoto (Windows Server 2008 R2 o versiones posteriores). De este modo, hasta 200 usuarios anónimos pueden tener acceso de manera simultánea a la demostración. Su demostración no debe usar datos de producción. La licencia de los suscriptores de Visual Studio se concede para que muestren sus aplicaciones a los usuarios finales. La demostración en Internet a través de Terminal Services (TS) o Servicios de Escritorio remoto (RDS) es el único escenario en que usuarios finales sin una suscripción de Visual Studio pueden interactuar con la aplicación de demostración si la licencia del software se obtuvo a través de suscripciones de Visual Studio.

Esto es además de los derechos de desarrollo y pruebas, en los que los suscriptores de Visual Studio pueden usar tantas conexiones a RDS o TS como sea necesario.

## <a name="enabling-rds-access"></a>Habilitación del acceso RDS
Los suscriptores de Visual Studio pueden aumentar el número de usuarios que pueden tener acceso a Windows Server a través de RDS escribiendo una clave de producto suministrada en la pestaña [Claves de producto](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) en el [portal de suscriptores](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Para obtener una clave de producto, conéctese a la página Claves de producto y desplácese hacia abajo a la versión de Windows Server que ejecuta. Busque "Conexiones de < usuario o dispositivo > de Servicios de Escritorio remoto de Windows Server < versión > R2" y haga clic en el vínculo **Claim Key** (Reclamar clave). Por ejemplo, si usa RDS en Windows Server 2012 R2 y su implementación usa CAL de usuario, elija "Conexiones de usuario de Servicios de Escritorio remoto de Windows Server 2012 (50)".
Hay disponibles cinco claves de cada tipo para Windows Server 2008 R2 y cada clave admitirá 20 conexiones. En el caso de Windows Server 2012 R2, se proporcionan cuatro claves de cada tipo y cada una admitirá 50 conexiones.

## <a name="to-enable-additional-connections-in-windows-server"></a>Para habilitar más conexiones en Windows Server:
1. Abra el Administrador de servidores.
2. Abra la lista de servidores en el panel de navegación izquierdo.
3. Haga clic con el botón derecho en su servidor de licencias y elija "Instalar licencias".
4. Siga los pasos del asistente.  Cuando seleccione el tipo de contrato, elija "Paquete de licencias (venta directa)" y escriba la clave de producto que obtuvo en Mi portal.

Los usuarios finales pueden conectarse para tener acceso a aplicaciones a través de RDS si se cumplen las condiciones siguientes:
- Los usuarios deben ser anónimos (en un estado no autenticado).
- Las conexiones deben realizarse a través de Internet.
- Se pueden usar hasta 200 conexiones de usuarios simultáneas para las demostraciones de la aplicación.
- Las claves de producto para habilitar las conexiones de usuarios las debe obtener un suscriptor de Visual Studio.

## <a name="support-resources"></a>Recursos de soporte técnico
- Para obtener ayuda con las ventas, las suscripciones, las cuentas y la facturación de suscripciones de Visual Studio, póngase en contacto con el [soporte técnico de suscripciones de Visual Studio](https://aka.ms/vssubscriberhelp).

## <a name="see-also"></a>Consulte también
- [Documentación de Windows Server](/windows-server/)
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Si necesita orientación para implementar RDS, vea la serie de blogs de varias partes sobre la **implementación de sesiones de Servicios de Escritorio remoto (RDS) 2012** en https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerf. 

Si tiene alguna pregunta, visite el [foro de Servicios de Escritorio remoto de Microsoft](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS).