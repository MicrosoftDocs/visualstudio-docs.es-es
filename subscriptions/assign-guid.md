---
title: Asignación de GUID específicos a suscriptores de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.date: 02/18/2021
ms.topic: conceptual
description: Obtenga información sobre cómo los administradores pueden asignar GUID de suscripción específicos a los suscriptores.
ms.openlocfilehash: 3c92a3e6cc35230f6bcf10320e92a50dc5ffb85b
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249682"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Asignación de suscripciones específicas en el Portal de administración de suscripciones de Visual Studio

Ahora, los administradores pueden usar el Portal de administración de Suscripciones de Visual Studio para asignar suscripciones específicas a suscriptores individuales.  Esto puede ser útil si una organización tiene personal o proveedores temporales que necesitan acceder a una suscripción durante un breve período.  Los administradores pueden asignar una suscripción que ya se haya utilizado parcialmente y dejar las nuevas para un uso más prolongado.  

Vea el vídeo o siga leyendo para saber cómo asignar identificadores únicos de suscripciones específicas a los usuarios. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Asignación de GUID de suscripción específicos a los usuarios

El proceso de asignación de suscripciones específicas a usuarios individuales implica aprovechar dos procesos de administración existentes para asignar identificadores únicos globales (GUID) de suscripción específicos a usuarios individuales.  En este proceso de tres pasos se incluyen la exportación de una lista de las suscripciones y asignaciones actuales, el uso de esa lista para identificar los GUID específicos que quiere asignar y el uso del proceso de adición en masa para cargar las nuevas asignaciones.

### <a name="export-your-subscriptions-information"></a>Exportación de la información de las suscripciones

Para realizar la exportación, siga estos pasos:
1. Inicie sesión en el [Portal de administración](https://manage.visualstudio.com).
2. Seleccione la pestaña **Exportar** y el archivo se descargará en la máquina local. El archivo incluirá el nombre del acuerdo que contiene las suscripciones de los usuarios, así como la fecha de la exportación.
> [!div class="mx-imgBorder"]
> ![Exportar suscriptores](_img/exporting-subscriptions/exporting-subscriptions.png "Haga clic en Exportar para guardar la lista de las suscripciones asignadas con información del suscriptor.")

### <a name="identify-the-guids-you-want-to-assign"></a>Identificación de los GUID que quiere asignar

Si ha usado la herramienta de exportación anteriormente, verá que se han agregado nuevos campos a la hoja de cálculo que se genera.  Esto le ayudará a determinar el estado de cada suscripción y cuáles de ellas quiere asignar a los usuarios.  

- **Estado de la suscripción**: en este campo se mostrarán los valores "asignado" o "sin asignar".  Si una suscripción tiene el estado "asignado", también tendrá información de usuario asociada, como el nombre, el correo electrónico, etc. 
- **Estado de uso**: en el estado de uso, se indicará "nuevo", lo que significa que la suscripción nunca se ha asignado a un usuario, o bien "usado", lo que indica que se ha asignado a un usuario en algún momento.  

Puede usar los valores de estos campos, junto con otra información de la hoja de cálculo, para determinar qué suscripciones quiere asignar a usuarios individuales. Puede aplicar un filtro en Excel para restringir la lista por estado, nivel de suscripción, fecha de expiración, etc. 

### <a name="upload-your-new-assignments"></a>Carga de las nuevas asignaciones

El paso final es descargar la plantilla **Agregar en masa**, rellenar la información necesaria para las suscripciones que quiera asignar y cargar la plantilla.  Para obtener una descripción completa de este proceso, consulte el artículo [Incorporación de varios usuarios](assign-license-bulk.md).  

> [!IMPORTANT]
> Para garantizar una carga correcta, compruebe que se cumplan los siguientes requisitos:
> - Está utilizando la plantilla vinculada en el cuadro de diálogo al seleccionar **Agregar en masa**.  No use una copia almacenada localmente de la plantilla, ya que puede que no contenga todos los campos obligatorios.  El uso de una plantilla antigua provocará un error de carga. 
> - Todos los campos mostrados como **necesarios** en la plantilla están completados.
> - No se muestran errores en la columna **Mensaje de error**.
> - Cada GUID se usa solo una vez en la plantilla. 
> - El nivel de suscripción de la plantilla coincide con la suscripción del GUID de la lista exportada. 
> - El GUID no se ha asignado ya a otro usuario de la lista exportada. 

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
### <a name="q-how-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>P: ¿Cómo puedo cambiar la suscripción que está asignada actualmente a un usuario individual?
R: Si quiere cambiar el GUID asignado a un usuario, primero deberá eliminar la suscripción para ese usuario.  Para más información, consulte el artículo [Eliminar suscripciones](delete-license.md).  Después de eliminar la suscripción para ese usuario, siga el proceso descrito anteriormente para exportar la lista y cargar la información de la nueva suscripción.  

## <a name="resources"></a>Recursos
- [Soporte de la suscripción de Visual Studio](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="see-also"></a>Consulte también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Ahora que ha asignado las suscripciones a los usuarios, descubra cómo realizar otras tareas de administración.
- [Asignación de suscripciones individuales](assign-license.md)
- [Asignación de varias suscripciones](assign-license-bulk.md)
- [Editar suscripciones](edit-license.md)
- [Eliminar suscripciones](delete-license.md)
- [Determinación del uso máximo](maximum-usage.md)


