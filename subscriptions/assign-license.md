---
Title: Assign licenses to Visual Studio Subscriptions | Microsoft Docs
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how administrators can assign licenses to subscribers
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: b82f02b968398d0a8d1ce4872ce00e8447a2ae4d
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Asignar licencias en el Portal de administración de suscripciones de Visual Studio

## <a name="assigning-a-single-user"></a>Asignar un solo usuario
Si tiene licencias disponibles para suscripciones de Visual Studio, puede asignarlas a usuarios nuevos para que tengan acceso a los beneficios de la suscripción. 
1.  Para asignar un solo suscriptor de Visual Studio, haga clic en **Agregar** en la parte superior de la tabla.

    ![Agregar suscriptor](_img\assign-license-add\assign-license-add.png)

2.  Escriba la información en los campos del formulario para el nuevo suscriptor. Si su organización usa Azure Active Directory, este campo actúa como una función de búsqueda para buscar personas en el directorio actual, por lo que puede seleccionar el usuario correcto entre los resultados de la búsqueda. Una vez que haya seleccionado a esa persona, se rellenarán automáticamente su nombre, correo electrónico de inicio de sesión y correo electrónico de notificación, como se ve a continuación. 

Si su organización tiene una dirección de correo electrónico para recibir mensajes diferente de la que se usa para iniciar sesión, puede especificarla aquí. Seleccione el hipervínculo "Different email for communication than sign-in?" ("¿Tiene un correo electrónico diferente al de inicio de sesión para la comunicación?"). 

Si desea que este suscriptor tenga acceso a las descargas de software cuando inicia sesión en el [portal de suscripciones de Visual Studio](https:/my.visualstudio.com?wt.mc_id=o~msft~docs), asegúrese de dejar activada la casilla Descargas. Si desactiva esta casilla, el usuario no tendrá acceso a las descargas de software, pero seguirá teniendo acceso a todas las demás ventajas incluidas en la suscripción. Cuando termine, haga clic en **Agregar**.

   ![Escribir la información del suscriptor](_img\assign-license-add\add-subscriber-1.png)

   ![Escribir la información del suscriptor](_img\assign-license-add\add-subscriber-2.png)

3.  Después de agregar el suscriptor, se enviará automáticamente un correo electrónico de asignación al nuevo suscriptor con instrucciones adicionales. Puede volver a enviar el correo electrónico de asignación en cualquier momento si selecciona el suscriptor y hace clic en el botón **Reenviar** en el menú superior.

    ![Suscriptor agregado](_img\assign-license-add\add-subscriber-complete.png)

## <a name="bulk-assignments"></a>Asignaciones en masa
1.  Para agregar varios suscriptores a la vez, vaya a la pestaña Suscriptores. En la cinta de la parte superior, haga clic en **Agregar en masa**. 

    ![Agregar en masa](_img\assign-license-add\bulk-assign-add.png)

2. La asignación en masa usa una plantilla de Microsoft Excel para cargar los suscriptores. En el cuadro de diálogo para cargar varios suscriptores, haga clic en **Descargar** para descargar la plantilla. Descargue siempre la versión más reciente de esta plantilla. Si usa una versión antigua, se puede producir un error en la carga masiva.

    ![Cargar varios suscriptores](_img\assign-license-add\bulk-assign-upload.png)

3.  En la hoja de cálculo de Excel, rellene los campos con la información de las personas a las que quiere asignar suscripciones. El campo Referencia es opcional. Si ha rellenado alguna parte de la plantilla de forma incorrecta, verá un mensaje de error que describe el problema. Guarde el archivo en el disco duro cuando haya acabado.
**Para garantizar una carga sin problemas, tenga en cuenta los siguientes procedimientos recomendados:**
    - Asegúrese de que ninguno de los campos del formulario contiene comas.
    - Quite los espacios delante y detrás de los campos del formulario, como los nombres de los usuarios.
    - Asegúrese de que los nombres de los usuarios no contienen espacios adicionales entre las partes de los nombres compuestos o los apellidos (por ejemplo, el nombre compuesto "Maggie May" no debe escribirse "Maggie  May", ya que el sistema no eliminará el espacio adicional).

   ![Plantilla para agregar en masa](_img\assign-license-add\bulk-template.png)

4.  Vuelva al Portal de administración de Suscripciones de Visual Studio y, en el cuadro de diálogo para cargar varios suscriptores, haga clic en **Examinar**. Vaya al archivo de Excel que ha guardado y haga clic en **Aceptar**. Verá el progreso de la carga en la pantalla. 

    ![Carga para agregar en masa](_img\assign-license-add\bulk-assign-upload-2.png)

Si la plantilla contiene errores, se producirá un error en la carga y se mostrarán los errores para que pueda corregir la plantilla e intentar de nuevo la carga en masa.

   ![Error en la carga](_img\assign-license-add\bulk-assign-upload-fail.png)

Cuando la carga se realice correctamente, verá la lista de suscriptores y un mensaje de confirmación.

   ![Carga completa](_img\assign-license-add\bulk-assign-upload-complete.png)