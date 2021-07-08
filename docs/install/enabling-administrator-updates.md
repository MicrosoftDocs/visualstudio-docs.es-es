---
title: Habilitación de actualizaciones de administrador para Visual Studio con Microsoft Endpoint Configuration Manager
titleSuffix: ''
description: Obtenga más información sobre cómo implementar actualizaciones de administrador en Visual Studio.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: affb5a0c78c1ad1e230c571485385d9f55fc2bec
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307458"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Habilitación de actualizaciones de administrador para Visual Studio con Microsoft Endpoint Configuration Manager

Microsoft Endpoint Configuration Manager (SCCM) puede administrar las actualizaciones de administrador de Visual Studio 2017 y Visual Studio 2019 mediante el flujo de trabajo de administración de actualización de software.

> [!NOTE]
> Para simplificar la documentación, el contenido siguiente se referirá colectivamente a los productos Visual Studio 2017, Visual Studio 2019 y Visual Studio 2022 como "Visual Studio".

Cuando Microsoft publica una nueva actualización de Visual Studio en Content Delivery Network (CDN), Microsoft publicará simultáneamente un paquete de actualización de administrador correspondiente en los servidores de Microsoft Update. Esto permitirá a un administrador distribuir la actualización de Visual Studio a través del [catálogo de Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) o [Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) (WSUS). Configuration Manager puede configurarse para sincronizar las actualizaciones del administrador de Visual Studio desde el catálogo WSUS en el servidor del sitio para, a continuación, descargar la actualización y distribuirla a los equipos cliente de Visual Studio en toda la organización. Para obtener más información sobre las correcciones presentes en cada versión de Visual Studio, consulte las [notas de la versión](/visualstudio/releases/2019/release-notes).

Para distribuir las actualizaciones de administrador de Visual Studio a través de Configuration Manager, deberá realizar estos dos pasos de preparación iniciales:
1. Habilite Configuration Manager para recibir notificaciones de actualización del administrador de Visual Studio. 
2. Habilite (o deshabilite) los equipos cliente para recibir las actualizaciones de administrador de Visual Studio desde Configuration Manager.

Después de realizar estos pasos, puede usar las funcionalidades de administración de actualizaciones de software de Configuration Manager para implementar las actualizaciones de administrador de Visual Studio. Los distintos tipos y características de las actualizaciones de administrador de Visual Studio se describen en [Aplicación de actualizaciones de administrador](../install/applying-administrator-updates.md), que proporciona instrucciones sobre cómo y cuándo se deben distribuir en toda la organización. Para obtener más información acerca de la funcionalidad y las opciones de Configuration Manager, vea [Implementar actualizaciones de software en Microsoft Endpoint Configuration Manager](/mem/configmgr/sum/deploy-use/deploy-software-updates).

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Habilitación de Configuration Manager para recibir notificaciones de actualización del administrador de Visual Studio

Para habilitar Configuration Manager para administrar las actualizaciones de administrador de Visual Studio, necesitará lo siguiente:

* Una versión con licencia actual de Windows Server que ejecute Microsoft Endpoint Configuration Manager (rama actual) y Windows Server Update Services (WSUS). No puede usar WSUS por sí mismo para implementar estas actualizaciones; se debe usar junto con Configuration Manager.

* El servidor WSUS de nivel superior de la jerarquía y el servidor de sitio Configuration Manager de nivel superior deben tener acceso a las direcciones URL y los puertos de Visual Studio que se enumeran aquí: [Instalación y uso de Visual Studio y de servicios de Azure detrás de un firewall o servidor proxy](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md).  

* Microsoft Endpoint Configuration Manager debe estar configurado para recibir notificaciones cuando estén disponibles los paquetes de actualización del administrador de Visual Studio.  Para ello, siga los pasos que se indican a continuación y, para obtener más información, consulte [Introducción a las actualizaciones de software en Configuration Manager](/mem/configmgr/sum/understand/software-updates-introduction).

  1. En la consola de Configuration Manager, seleccione **Administración** (abajo a la izquierda), luego seleccione **Configuración del sitio** (en el centro a la izquierda), luego **Sitios** y seleccione el servidor de sitio.

  2. En la cinta de opciones de la pestaña **Inicio**, en la parte superior, en el botón grupo **Configuración**, seleccione **Configurar componentes de sitio** y, a continuación, seleccione **Punto de actualización de software**.

  3. En el cuadro de diálogo **Propiedades de componente de punto de actualización de software**:

        * En la pestaña **Productos**, en la jerarquía **Herramientas de desarrollo, Entornos de ejecución y Redistribuibles**, elija las versiones de Visual Studio que desea sincronizar.

        * En la pestaña **Clasificaciones**, asegúrese de que están seleccionadas las opciones "Actualizaciones de seguridad", "Paquetes de características" y "Actualizaciones".

  4. A continuación, sincronice las actualizaciones de software con el servidor WSUS eligiendo **Biblioteca de software** (abajo a la izquierda) y, a continuación, en la cinta de opciones de la pestaña **Inicio**, en la parte superior, seleccione el botón **Sincronizar actualizaciones de software**. La sincronización de las actualizaciones de software hará que las actualizaciones disponibles del administrador de Visual Studio estén visibles en la consola de Configuration Manager y puedan implementarse desde ahí.

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>Habilitación (o deshabilitación) de la capacidad de los equipos cliente para recibir las actualizaciones de administrador de Visual Studio desde Configuration Manager

Para permitir que un equipo cliente acepte actualizaciones de administrador de Visual Studio, debe asegurarse de que la utilidad de detección de clientes de Visual Studio está instalada correctamente y debe establecer una clave del Registro para permitir que el cliente reciba actualizaciones de administrador.  

### <a name="visual-studio-client-detector-utility"></a>Utilidad de detección de clientes de Visual Studio

[Visual Studio Client Detector Utility](https://support.microsoft.com/help/5001148) debe estar instalado en los equipos del cliente para que las actualizaciones de administrador se reconozcan y reciban correctamente. Esta utilidad se incluyó con todas las actualizaciones de producto de Visual Studio 2017 y Visual Studio 2019 que se publicaron el 12 de mayo de 2020 o después, se incluye como un requisito previo con todas las actualizaciones del administrador de Visual Studio y también está disponible en el [Catálogo de Microsoft Update](https://catalog.update.microsoft.com) para instalarse de forma independiente.

### <a name="encoding-administrator-intent-on-the-client-machines"></a>Codificación de la intención del administrador en los equipos cliente

Los equipos cliente deben estar habilitados para recibir actualizaciones de administrador. Este paso es necesario para asegurarse de que las actualizaciones no se envíen de forma involuntaria o accidental a equipos clientes desprevenidos.

La clave **AdministratorUpdatesEnabled**  está diseñada para que el administrador codifique la intención del administrador. Esta clave puede estar en cualquiera de las ubicaciones estándar de Visual Studio, tal y como se describe en la documentación [Establecimiento de valores predeterminados para implementaciones empresariales de Visual Studio](/visualstudio/install/set-defaults-for-enterprise-deployments). Se requiere acceso de administrador en el equipo cliente para crear y establecer el valor de esta clave.

* Para configurar el equipo cliente para que acepte las actualizaciones de administrador, establezca la clave **AdministratorUpdatesEnabled** REG_DWORD en  **1**.
* Si falta la clave  **AdministratorUpdatesEnabled** REG_DWORD **o está establecida en 0**, se bloqueará la aplicación de actualizaciones de administrador en el equipo cliente.

## <a name="feedback-and-support"></a>Comentarios y soporte técnico

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Puede usar los métodos siguientes para proporcionar comentarios acerca de las actualizaciones de administrador de Visual Studio o notificar problemas que afecten a las actualizaciones:

* Consulte las orientaciones de [Solución de problemas de instalación y actualización de Visual Studio](../install/troubleshooting-installation-issues.md).
* Formule preguntas a la comunidad en el [Foro de preguntas y respuestas de instalación de Visual Studio](/answers/topics/vs-setup.html).
* Vaya a la [página de soporte técnico de Visual Studio](https://visualstudio.microsoft.com/vs/support/) y compruebe si el problema aparece en las preguntas más frecuentes.  También puede seleccionar el botón del [vínculo de soporte técnico](https://visualstudio.microsoft.com/vs/support/#talktous) para obtener ayuda por chat.
* [Proporcione comentarios sobre las características o notifique un problema](https://aka.ms/vs/wsus/feedback) al equipo de Visual Studio con respecto a esta experiencia de habilitación de las actualizaciones de administrador.
* Póngase en contacto con el responsable técnico de cuentas de su organización para Microsoft.

## <a name="see-also"></a>Consulte también

* [Aplicación de las actualizaciones de administrador](../install/applying-administrator-updates.md)
* [Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md)
* [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/productinfo/vs-servicing-vs)
* [Notas de la versión de Visual Studio 2019](/visualstudio/releases/2019/release-notes)
* [Notas de la versión de Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Instalación de Visual Studio](../install/install-visual-studio.md)
* [Preguntas más frecuentes del catálogo de Microsoft Update](https://www.catalog.update.microsoft.com/faq.aspx)
* [Documentación de Microsoft Endpoint Configuration Manager (SCCM)](/mem/configmgr)
* [Importación de actualizaciones desde el catálogo de Microsoft Update](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Documentación de Windows Server Update Services (WSUS)](/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
