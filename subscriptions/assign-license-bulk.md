---
title: Asignación de licencias a grupos de usuarios para suscripciones de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 05/10/2020
ms.topic: conceptual
description: Obtenga información acerca de cómo los administradores pueden asignar licencias a varios suscriptores mediante la característica de adición masiva o los grupos de Microsoft Azure Active Directory.
ms.openlocfilehash: 41dd3049c790ac790b46d12b976eb3ab6457fcb2
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182903"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Asignación de suscripciones a varios usuarios
El Portal de administración de suscripciones permite agregar usuarios de uno en uno o en grupos grandes.  Para agregar usuarios individuales, consulte [Agregar usuarios individuales](assign-license.md).

Para agregar grandes grupos de usuarios, puede usar la característica Agregar en masa, o bien, si su organización usa Microsoft Azure Active Directory (Azure AD), puede usar grupos de Azure AD. En este artículo se explica el proceso de ambas opciones. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Uso de la adición en masa para asignar suscripciones
1. Inicie sesión en el Portal de administración de suscripciones de Visual Studio en https://manage.visualstudio.com.

2. Para agregar varios suscriptores a la vez, vaya a la pestaña **Administrar suscriptores**. Elija la pestaña **Agregar** y, a continuación, elija **Agregar en masa** en el menú desplegable.  

2. En la adición en masa se usa una plantilla de Microsoft Excel para cargar información de los suscriptores. En el cuadro de diálogo para cargar varios suscriptores, haga clic en **Descargar** para descargar la plantilla.
   > [!div class="mx-imgBorder"]
   > ![Descarga de la plantilla de Excel para cargar varios suscriptores](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Descargue siempre la versión más reciente de esta plantilla. Si usa una versión antigua, se puede producir un error en la carga masiva.

3. En la hoja de cálculo de Excel, rellene los campos con la información de las personas a las que quiere asignar suscripciones. (El campo *Referencia* es opcional). Guarde el archivo localmente cuando haya terminado.

    > [!NOTE]
    > Uno de los campos de la plantilla permite a los administradores habilitar o deshabilitar la capacidad de los suscriptores de descargar software.  Al deshabilitar las descargas también se deshabilita su acceso a las claves de producto.

   Para garantizar una carga sin problemas, tenga en cuenta los siguientes procedimientos recomendados:

    - Asegúrese de que ninguno de los campos del formulario contiene comas.
    - Quite los espacios de delante y detrás de los campos del formulario.
    - Asegúrese de que los nombres de los usuarios no contienen espacios adicionales entre las dos partes de los nombres compuestos (por ejemplo, el nombre compuesto "Maggie May" se debe escribir como "MaggieMay", ya que el sistema no elimina el espacio adicional).
    - Asegúrese de que se han completado todos los campos obligatorios. 
    - Compruebe la columna **Mensaje de error**.  Si aparece algún error, resuélvalo antes de intentar cargar el archivo. 

4. Vuelva al portal de administración de suscripciones de Visual Studio. En el cuadro de diálogo **Cargar varios suscriptores**, haga clic en **Examinar**.
   > [!div class="mx-imgBorder"]
   > ![Examen de la plantilla guardada para cargar varios suscriptores](media/bulk-add-browse-saved-template.png)

5. Vaya al archivo de Excel que ha guardado y haga clic en **Aceptar**.
   > [!div class="mx-imgBorder"]
   > ![Carga de la plantilla de Excel para cargar varios suscriptores](media/bulk-upload-subscribers.png)

    Aparece un cuadro de diálogo de progreso de carga.

    Si la plantilla contiene errores, se produce un error en la carga y se muestran los errores para que pueda corregir la plantilla e intentar de nuevo la carga en masa.
   > [!div class="mx-imgBorder"]
   > ![Mensaje de error si se produce un error en la carga de varios suscriptores](_img/assign-license-bulk/bulk-add-upload-failure.png)

   Si se produce un error, siga estos pasos:
   1. Abra el archivo de Excel que ha creado, corrija los problemas y guarde el archivo.
   0. Vuelva al Portal de administración y elija **Agregar**.
   0. Seleccione **Agregar en masa**.
   0. Como ya se ha guardado el archivo de Excel, no es necesario descargar la plantilla.  Haga clic en **Examinar**, busque el archivo que acaba de guardar y haga clic en **Abrir**.
   0. Haga clic en **Aceptar**.


    Cuando la carga se realice correctamente, verá la lista de suscriptores y un mensaje de confirmación.
   > [!div class="mx-imgBorder"]
   > ![Mensaje de confirmación si la carga de varios suscriptores se realiza correctamente](_img/assign-license-bulk/bulk-add-upload-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Uso de grupos de Azure Active Directory para asignar suscripciones 
Con esta característica, resulta más sencillo mantenerse al tanto de las asignaciones de suscripciones. Puede agregar grupos de Azure Active Directory en el Portal de administración de suscripciones, lo que garantizará que todas las personas del grupo tengan asignada una suscripción. Además, para que sea más fácil, cuando los usuarios dejen la organización y se quiten de Azure Active Directory, también se quitará el acceso a las suscripciones. 


> [!IMPORTANT]
>
> Se aplican las siguientes limitaciones al uso de grupos de Azure AD para agregar suscriptores:
> - El administrador debe ser miembro del inquilino de AAD al agregar inicialmente un grupo al portal de administración.  Una vez agregado el grupo, los cambios en la pertenencia de los grupos no requieren la intervención del administrador. 
> - Los grupos deben contener al menos un miembro.  No se admiten grupos vacíos.
> - Los grupos deben tener menos de 1000 usuarios. 
> - Todos los usuarios deben estar en el nivel superior del grupo.  No se admiten grupos anidados.
> - Solo se admiten acuerdos de confianza.
> - Todos los miembros del grupo deben tener una dirección de correo electrónico asociada a su cuenta de Azure AD.
> - Las notificaciones de suscripciones agregadas con grupos de Azure AD no se pueden enviar a direcciones de correo electrónico independientes.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Inicie sesión en el Portal de administración de suscripciones de Visual Studio en [https://manage.visualstudio.com](https://manage.visualstudio.com).

2. Para agregar varios suscriptores a la vez, vaya a la pestaña **Administrar suscriptores**.

3. Elija la pestaña **Agregar** y, después, seleccione **Grupo de Azure Active Directory** en el menú desplegable.  

   > [!div class="mx-imgBorder"]
   > ![Selección de adición masiva mediante Azure AD](_img/assign-license-bulk/bulk-add-aad.png)

4. En el campo de formulario, comience a escribir el nombre del grupo de Azure AD que quiera agregar. De este modo, se buscarán los grupos de Azure AD disponibles dentro de la organización. 

5. Al seleccionar el grupo, el campo se rellenará automáticamente con el nombre del grupo. Tendrá la opción de ver los usuarios de ese grupo antes de agregarlos. A continuación, puede elegir el nivel de suscripción, los derechos de descarga y las preferencias de comunicación para el grupo. Si lo desea, puede agregar detalles en el campo de referencia. 

   > [!div class="mx-imgBorder"]
   > ![Selección de adición masiva mediante Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png)

6. Haga clic en **Agregar** y, luego, en **Confirmar**. 

7. Para ver el grupo agregado, desplácese a la parte inferior de la lista de usuarios.  

8. Seleccione **Ver suscriptores** para mostrar los miembros del grupo. Puede ver los detalles de los suscriptores del grupo, pero no puede hacer modificaciones en los suscriptores ni en las suscripciones a las que están asignados.    

> [!NOTE]
> Si ya se han asignado las suscripciones individualmente a los usuarios que se agregan posteriormente como parte de un grupo de Azure AD, se agregarán como parte del grupo y ya no se mostrarán individualmente. Sin embargo, si la suscripción individual es para un nivel de suscripción distinto, tendrá dos suscripciones.  Ejemplo:  si un usuario tiene una suscripción individual de Visual Studio Professional y es miembro de un grupo al que se asignan suscripciones de Visual Studio Enterprise, este usuario tendrá ambas.  


## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>P: ¿Puedo elegir varios niveles de suscripción para asignarlos dentro de un grupo de Azure AD? 
R: No, todos los miembros del grupo reciben la misma suscripción. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>P: ¿Puedo editar los detalles de suscriptor de los usuarios agregados en un grupo de Azure AD?  
R: No, para modificar la información de un suscriptor individual, deberá quitarlo del grupo de seguridad de Azure AD y asignarle una suscripción individualmente.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>P: He agregado a alguien al grupo de seguridad de Azure AD, pero no lo veo en el Portal de administración de suscripciones ni tiene una suscripción. ¿Por qué no?  
R: En función de cómo haya configurado la organización Azure AD, pueden producirse retrasos de hasta 24 horas antes de que se agregue el usuario. Si han pasado más de 24 horas, [póngase en contacto con el servicio de soporte técnico](https://visualstudio.microsoft.com/support/support-overview-vs).  

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentación de Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentación de Azure](https://docs.microsoft.com/azure/)
- [Documentación de Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
- ¿Tiene solo que agregar uno o dos suscriptores?  Consulte [Agregar usuarios individuales](assign-license.md).
- ¿Necesita ayuda? Póngase en contacto con el [soporte técnico de administración y suscripciones de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).
