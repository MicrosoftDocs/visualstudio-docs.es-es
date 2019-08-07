---
title: Asignación de licencias a grupos de usuarios para suscripciones de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Conozca cómo los administradores pueden asignar licencias a varios suscriptores.
ms.openlocfilehash: 7d54dcf3cf3e7fea7845a4e9a0053de4ba734ae9
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2019
ms.locfileid: "68610525"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Asignación de suscripciones a varios usuarios
El Portal de administración de suscripciones permite agregar usuarios de uno en uno o en grupos grandes.  Para agregar usuarios individuales, consulte [Agregar usuarios individuales](assign-license.md).

## <a name="use-bulk-add-to-assign-subscriptions"></a>Uso de la adición en masa para asignar suscripciones
1. Inicie sesión en el Portal de administración de suscripciones de Visual Studio en https://manage.visualstudio.com.
2. Para agregar varios suscriptores a la vez, vaya a la pestaña **Administrar suscriptores**. En la cinta de la parte superior, haga clic en **Agregar en masa**.
   > [!div class="mx-imgBorder"]
   > ![Adición de varios suscriptores](media/add-multiple-subscribers.png)

2. En la adición en masa se usa una plantilla de Microsoft Excel para cargar información de los suscriptores. En el cuadro de diálogo para cargar varios suscriptores, haga clic en **Descargar** para descargar la plantilla.
   > [!div class="mx-imgBorder"]
   > ![Descarga de la plantilla de Excel para cargar varios suscriptores](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Descargue siempre la versión más reciente de esta plantilla. Si usa una versión antigua, se puede producir un error en la carga masiva.

3. En la hoja de cálculo de Excel, rellene los campos con la información de las personas a las que quiere asignar suscripciones. (El campo *Referencia* es opcional). Guarde el archivo localmente cuando haya terminado.

   Para garantizar una carga sin problemas, tenga en cuenta los siguientes procedimientos recomendados:

    - Asegúrese de que ninguno de los campos del formulario contiene comas.
    - Quite los espacios de delante y detrás de los campos del formulario.
    - Asegúrese de que los nombres de los usuarios no contienen espacios adicionales entre las dos partes de los nombres compuestos (por ejemplo, el nombre compuesto "Maggie May" se debe escribir como "MaggieMay", ya que el sistema no elimina el espacio adicional).

4. Vuelva al portal de administración de suscripciones de Visual Studio. En el cuadro de diálogo **Cargar varios suscriptores**, haga clic en **Examinar**.
   > [!div class="mx-imgBorder"]
   > ![Examen de la plantilla guardada para cargar varios suscriptores](media/bulk-add-browse-saved-template.png)

5. Vaya al archivo de Excel que ha guardado y haga clic en **Aceptar**.
   > [!div class="mx-imgBorder"]
   > ![Carga de la plantilla de Excel para cargar varios suscriptores](media/bulk-upload-subscribers.png)

    Aparece un cuadro de diálogo de progreso de carga.

    Si la plantilla contiene errores, se produce un error en la carga y se muestran los errores para que pueda corregir la plantilla e intentar de nuevo la carga en masa.
   > [!div class="mx-imgBorder"]
   > ![Mensaje de error si se produce un error en la carga de varios suscriptores](media/bulk-add-template-failed.png)

    Cuando la carga se realice correctamente, verá la lista de suscriptores y un mensaje de confirmación.
   > [!div class="mx-imgBorder"]
   > ![Mensaje de confirmación si la carga de varios suscriptores se realiza correctamente](media/bulk-add-template-success.png)

## <a name="next-steps"></a>Pasos siguientes
- ¿Tiene solo que agregar uno o dos suscriptores?  Consulte [Agregar usuarios individuales](assign-license.md).
- Aprenda a [editar](edit-license.md) las suscripciones existentes.
- ¿Necesita ayuda? Póngase en contacto con el [soporte técnico de administración y suscripciones de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).
