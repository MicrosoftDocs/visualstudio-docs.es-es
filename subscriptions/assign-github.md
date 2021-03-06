---
title: Asignación de suscripciones de Visual Studio con GitHub Enterprise | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/03/2021
ms.topic: conceptual
description: Administración de suscripciones en suscripciones de Visual Studio con GitHub Enterprise
ms.openlocfilehash: c66932d9f0da5e7dbca6dccb8efc911b1453bb8e
ms.sourcegitcommit: d8d230791890cda532c263d04288dc13d2261c7f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2021
ms.locfileid: "104757664"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>Administración de suscripciones de Visual Studio con GitHub Enterprise
Los clientes que tengan contratos Enterprise (EA) con Microsoft pueden comprar una nueva oferta de suscripciones que junta las suscripciones estándar de Visual Studio y GitHub Enterprise. Es la forma fácil y económica para los suscriptores de Visual Studio de adquirir GitHub Enterprise. 

Cuando la organización compra suscripciones de Visual Studio con GitHub Enterprise, se aprovisionan y se administran en dos partes.

## <a name="manage-visual-studio-subscriptions"></a>Administración de suscripciones de Visual Studio
Cuando la organización compra suscripciones de Visual Studio con GitHub Enterprise, la parte de Visual Studio de la suscripción se aprovisiona inmediatamente y las suscripciones están disponibles para asignarlas y administrarlas en el portal [Administración de suscripciones](https://manage.visualstudio.com) de Visual Studio. Después de asignar una suscripción de Visual Studio con GitHub Enterprise, el suscriptor recibirá un correo electrónico en el que se le indica que puede acceder a su suscripción de Visual Studio en <https://my.visualstudio.com/subscriptions>.

Para obtener más información sobre la administración de suscripciones de Visual Studio, vea estos temas:
- [Uso del portal de administración](using-admin-portal.md)
- [Asignación de suscripciones](assign-license.md)
- [Edición de suscripciones](edit-license.md)
- [Eliminación de suscripciones](delete-license.md)
- [Sobreasignaciones](handle-overclaimed-license.md)

> [!Important]
> Si los administradores de suscripciones de Visual Studio asignan las suscripciones de Visual Studio con GitHub Enterprise antes de realizar la compra, no se notificará a GitHub que quiere crear una cuenta de GitHub Enterprise.  Antes de asignar suscripciones, se debe realizar **una compra de al menos una** suscripción de Visual Studio con GitHub Enterprise.

## <a name="moving-to-visual-studio-with-github-enterprise"></a>Traslado de Visual Studio con GitHub Enterprise
Si su organización compra suscripciones de Visual Studio con paquetes de GitHub Enterprise después de haber asignado las suscripciones estándar de Visual Studio Enterprise y Visual Studio Professional, el portal de administración contiene una característica que le ayuda a trasladar los suscriptores existentes a la instancia de Visual Studio Enterprise correspondiente con GitHub Enterprise o Visual Studio Professional con las suscripciones de GitHub Enterprise.  Por ejemplo, los suscriptores con suscripciones Visual Studio Professional se moverán a Visual Studio Professional con las suscripciones de GitHub Enterprise. En el panel de la barra de la izquierda "Información general" verá el siguiente icono:

   > [!div class="mx-imgBorder"]
   > ![Botón Mover ahora](_img/assign-github/move-now.png "Haga clic en "Mover ahora" para actualizar las suscripciones a Visual Studio con las suscripciones de GitHub Enterprise.")

> [!IMPORTANT]
> Como se mencionó anteriormente, se mantendrán los datos del suscriptor, el historial y el identificador de suscripción existentes, y las ventajas que hayan activado no se interrumpirán debido a este movimiento.  
>
> (Esta característica se implementa en fases y puede que no esté disponible de inmediato en sus contratos).

Al hacer clic en el botón **Mover ahora**, un panel emergente le presentará recomendaciones sobre cómo mover las suscripciones Enterprise o Professional:

   > [!div class="mx-imgBorder"]
   > ![Panel Volar hacia fuera](_img/assign-github/fly-out.png)

En este icono, puede revisar los suscriptores afectados y especificar si desea notificarles que recibirán una notificación por correo electrónico una vez completado el traslado.  En este correo electrónico se informa a los suscriptores de que sus ventajas permanecen inalteradas y les anima a empezar a configurar una presencia en GitHub.  

Después de hacer clic en el botón para **Move all subscribers** (Mover todos los suscriptores), confirmará las selecciones y esperará unos segundos para que se complete el cambio de la suscripción.  Si es aplicable, tendrá que realizar estos pasos para las suscripciones Professional y Enterprise por separado.  


## <a name="what-is-the-visual-studio-with-github-enterprise-setup-process"></a>¿Qué es el proceso de configuración de Visual Studio con GitHub Enterprise?
GitHub Enterprise se configura y se administra de forma independiente de las suscripciones de Visual Studio. Tras la compra de una suscripción de Visual Studio con GitHub Enterprise, se inicia un proceso de configuración de la cuenta de GitHub Enterprise en paralelo, pero independiente, al establecimiento de un contrato en [manage.visualstudio.com](https://manage.visualstudio.com). El establecimiento de esta cuenta de GitHub Enterprise puede tardar un tiempo. 

Una vez que la empresa ha configurado una cuenta de GitHub Enterprise, los suscriptores a los que se les hayan asignado suscripciones de Visual Studio con GitHub Enterprise recibirán un correo electrónico de GitHub en el que se les notificará que sus suscripciones de Visual Studio se han vinculado. Después de que los suscriptores reciban este correo electrónico, podrán ponerse en contacto con el administrador de la organización de GitHub para recibir una invitación a la organización adecuada.

Para obtener más detalles sobre la configuración de GitHub Enterprise, consulte [documentación del suscriptor](access-github.md).   

## <a name="manage-github-enterprise-subscriptions"></a>Administración de suscripciones de GitHub Enterprise
Cuando se compran suscripciones de GitHub Enterprise, GitHub se asocia con los clientes para ayudarlos a crear y configurar las organizaciones que accederán a GitHub y a identificar a los administradores.  A continuación, esos administradores reciben una notificación en que se les comunica que se han configurado como administradores.  

Puesto que este proceso es más complejo, pueden pasar varios días tras la compra de las suscripciones antes de que las organizaciones y los administradores estén completamente configurados.

GitHub está disponible como GitHub.com basado en la nube o como el servidor de GitHub Enterprise de instalación local.  Los procesos para administrar las dos versiones son diferentes.  GitHub ofrece una variedad de temas de ayuda y guías del administrador que le ayudarán a administrar las suscripciones de GitHub Enterprise.  A continuación, hemos incluido vínculos a temas seleccionados.  

## <a name="support-resources"></a>Recursos de soporte técnico
- Obtenga más información sobre la asignación de GitHub en la [documentación de GitHub](https://docs.github.com/en/github/setting-up-and-managing-your-enterprise-account/managing-licenses-for-the-github-enterprise-and-visual-studio-bundle).
- Encuentre respuestas a preguntas sobre una amplia variedad de temas de GitHub en la [Ayuda de GitHub](https://help.github.com/en).
- Obtenga ayuda de otros usuarios de GitHub en el [Foro de la comunidad de GitHub](https://github.community/).
- Para obtener ayuda con la administración de suscripciones de Visual Studio, póngase en contacto el [soporte técnico de suscripciones de Visual Studio](https://aka.ms/vsadminhelp).
- ¿Tiene alguna pregunta sobre el IDE de Visual Studio, Azure DevOps Services u otros productos o servicios de Visual Studio?  Visite el [soporte técnico de Visual Studio](https://visualstudio.microsoft.com/support/).
- Obtenga [soporte técnico](https://support.microsoft.com/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) para GitHub Enterprise.   

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Obtenga más información sobre la administración de suscripciones de Visual Studio.
- [Asignación de suscripciones individuales](assign-license.md)
- [Asignación de varias suscripciones](assign-license-bulk.md)
- [Editar suscripciones](edit-license.md)
- [Eliminar suscripciones](delete-license.md)
- [Determinación del uso máximo](maximum-usage.md)

Para obtener más información sobre cómo administrar las suscripciones de Visual Studio con GitHub Enterprise, visite el [portal de administración de suscripciones](https://visualstudio.microsoft.com/subscriptions-administration/) de Visual Studio.