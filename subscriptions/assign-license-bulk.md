---
title: Asignación de licencias a grupos de usuarios para suscripciones de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 10/22/2020
ms.topic: how-to
description: Obtenga información sobre cómo los administradores pueden asignar licencias a varios suscriptores mediante la característica de adición masiva o los grupos de Microsoft Azure Active Directory.
ms.openlocfilehash: 6cb3613d76faca2adc9c6e946f6a8ec2c73770f1
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467549"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Asignación de suscripciones a varios usuarios
El Portal de administración de suscripciones permite agregar usuarios de uno en uno o en grupos grandes.  Para agregar usuarios individuales, consulte [Agregar usuarios individuales](assign-license.md).

Para agregar grandes grupos de usuarios, puede usar la característica Agregar en masa, o bien, si su organización usa Microsoft Azure Active Directory (Azure AD), puede usar grupos de Azure AD. En este artículo se explica el proceso de ambas opciones.  Vea este vídeo o siga leyendo para saber más sobre la característica de adición en masa. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Uso de la adición en masa para asignar suscripciones
1. Inicie sesión en el Portal de administración de suscripciones de Visual Studio en <https://manage.visualstudio.com>.

1. Para agregar varios suscriptores a la vez, vaya a la pestaña **Administrar suscriptores** . Elija la pestaña **Agregar** y, a continuación, elija **Agregar en masa** en el menú desplegable.  

1. En la adición en masa se usa una plantilla de Microsoft Excel para cargar información de los suscriptores. En el cuadro de diálogo Upload Multiple Subscribers (Cargar varios suscriptores), seleccione **Descargar** para descargar la plantilla.
   > [!div class="mx-imgBorder"]
   > ![Descarga de la plantilla de Excel para cargar varios suscriptores](media/download-template-upload-subscribers.png "Descargue la plantilla de Excel en blanco para iniciar el proceso de asignación en masa.")
   >
   > [!NOTE]
   > Descargue siempre la versión más reciente de esta plantilla. Si usa una versión antigua, se puede producir un error en la carga masiva.

1. En la hoja de cálculo de Excel, rellene los campos con la información de las personas a las que quiere asignar suscripciones. (El campo *Referencia* es opcional). Guarde el archivo localmente cuando haya terminado.

    > [!NOTE]
    > Uno de los campos de la plantilla permite a los administradores habilitar o deshabilitar la capacidad de los suscriptores de descargar software.  Al deshabilitar las descargas también se deshabilita su acceso a las claves de producto.

   Para garantizar una carga sin problemas, tenga en cuenta los siguientes procedimientos recomendados:

    - Asegúrese de que ninguno de los campos del formulario contiene comas.
    - Quite los espacios de delante y detrás de los campos del formulario.
    - Asegúrese de que los nombres de los usuarios no contienen espacios adicionales entre las dos partes de los nombres compuestos (por ejemplo, el nombre compuesto "Maggie May" se debe escribir como "MaggieMay", ya que el sistema no elimina el espacio adicional).
    - Asegúrese de que se han completado todos los campos obligatorios. 
    - Compruebe la columna **Mensaje de error** .  Si aparece algún error, resuélvalo antes de intentar cargar el archivo. 

1. Vuelva al portal de administración de suscripciones de Visual Studio. En el cuadro de diálogo **Upload Multiple Subscribers** (Cargar varios suscriptores), haga clic en **Examinar** .
   > [!div class="mx-imgBorder"]
   > ![Examen de la plantilla guardada para cargar varios suscriptores](media/bulk-add-browse-saved-template.png "Puede desplazarse hasta la ubicación del archivo, o bien arrastrarlo y colocarlo en este cuadro de diálogo.")

1. Vaya al archivo de Excel que ha guardado y seleccione **Aceptar** .
   > [!div class="mx-imgBorder"]
   > ![Carga de la plantilla de Excel para cargar varios suscriptores](media/bulk-upload-subscribers.png "La plantilla con los datos aparecerá aquí.  Seleccione Aceptar para iniciar la carga.")

    Aparece un cuadro de diálogo de progreso de carga.

    Si la plantilla contiene errores, se produce un error en la carga y se muestran los errores para que pueda corregir la plantilla e intentar de nuevo la carga en masa.
   > [!div class="mx-imgBorder"]
   > ![Mensaje de error si se produce un error en la carga de varios suscriptores](_img/assign-license-bulk/bulk-add-upload-failure.png "Este mensaje aparecerá si el archivo que ha cargado contenía errores.  Resuelva los errores y vuelva a realizar el proceso de adición en masa.")

   Si se produce un error, siga estos pasos:
   1. Abra el archivo de Excel que ha creado, corrija los problemas y guarde el archivo.
   0. Vuelva al portal de administración y descarte el mensaje de error.
   0. Haga clic en **Agregar** .
   0. Seleccione **Agregar en masa** .
   0. Como ya se ha guardado el archivo de Excel, no es necesario descargar la plantilla.  Seleccione **Examinar** , busque el archivo que acaba de guardar y seleccione **Abrir** .
   0. Seleccione **Aceptar** .


    Cuando la carga se realice correctamente, verá la lista de suscriptores y un mensaje de confirmación.
   > [!div class="mx-imgBorder"]
   > ![Mensaje de confirmación si la carga de varios suscriptores se realiza correctamente](_img/assign-license-bulk/bulk-add-upload-success.png "Cuando la carga se complete correctamente, recibirá un mensaje de confirmación.")

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Uso de grupos de Azure Active Directory para asignar suscripciones 
Con esta característica, resulta más sencillo mantenerse al tanto de las asignaciones de suscripciones. Puede agregar grupos de Azure Active Directory en el Portal de administración de suscripciones, lo que garantizará que todas las personas del grupo tengan asignada una suscripción. Además, para que sea más fácil, cuando los usuarios dejen la organización y se quiten de Azure Active Directory, también se quitará el acceso a las suscripciones. 


> [!IMPORTANT]
>
> Se aplican las siguientes limitaciones al uso de grupos de Azure AD para agregar suscriptores:
> - El administrador debe ser miembro del inquilino de AAD al agregar inicialmente un grupo al portal de administradores.  Una vez agregado el grupo, los cambios en la pertenencia de los grupos no requieren la intervención del administrador. 
> - Los grupos deben contener al menos un miembro.  No se admiten grupos vacíos.
> - Los grupos deben tener menos de 1000 usuarios. 
> - Todos los usuarios deben estar en el nivel superior del grupo.  No se admiten grupos anidados.
> - Solo se admiten acuerdos de confianza.
> - Todos los miembros del grupo deben tener una dirección de correo electrónico asociada a su cuenta de Azure AD.
> - Las notificaciones de suscripciones agregadas con grupos de Azure AD no se pueden enviar a direcciones de correo electrónico independientes.  

Vea este vídeo o siga leyendo para saber cómo agregar suscriptores mediante la característica de grupo de Azure Active Directory. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Inicie sesión en el Portal de administración de suscripciones de Visual Studio en [https://manage.visualstudio.com](https://manage.visualstudio.com).

2. Para agregar varios suscriptores a la vez, vaya a la pestaña **Administrar suscriptores** .

3. Elija la pestaña **Agregar** y, después, seleccione **Grupo de Azure Active Directory** en el menú desplegable.  

   > [!div class="mx-imgBorder"]
   > ![Selección de adición masiva mediante Azure AD](_img/assign-license-bulk/bulk-add-aad.png "Elija la característica Adición en masa mediante Azure AD para extraer suscriptores del grupo de Azure Active Directory.")

4. En el campo de formulario, comience a escribir el nombre del grupo de Azure AD que quiera agregar. De este modo, se buscarán los grupos de Azure AD disponibles dentro de la organización. 

5. Al seleccionar el grupo, el campo se rellenará automáticamente con el nombre del grupo. Tendrá la opción de ver los usuarios de ese grupo antes de agregarlos. A continuación, puede elegir el nivel de suscripción, los derechos de descarga y las preferencias de comunicación para el grupo. Si lo desea, puede agregar detalles en el campo de referencia. 

   > [!div class="mx-imgBorder"]
   > ![Selección del grupo de Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png "Elija el nombre del grupo de Azure AD para agregar suscriptores de ese grupo.")

6. Seleccione **Agregar** y, luego, **Confirmar** . 

7. Para ver el grupo agregado, desplácese a la parte inferior de la lista de usuarios.  

8. Seleccione **Ver suscriptores** para mostrar los miembros del grupo. Puede ver los detalles de los suscriptores del grupo, pero no puede hacer modificaciones en los suscriptores ni en las suscripciones a las que están asignados.    

> [!NOTE]
> Si ya se han asignado las suscripciones individualmente a los usuarios que se agregan posteriormente como parte de un grupo de Azure AD, se agregarán como parte del grupo y ya no se mostrarán individualmente. Sin embargo, si la suscripción individual es para un nivel de suscripción distinto, tendrá dos suscripciones.  Ejemplo:  si un usuario tiene una suscripción individual de Visual Studio Professional y es miembro de un grupo al que se asignan suscripciones de Visual Studio Enterprise, este usuario tendrá ambas.  
>
> Si quita un suscriptor de un grupo de Azure Active Directory que tiene suscripciones asignadas, la actualización puede tardar hasta 24 horas en reflejarse en el portal de administradores. 


## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>P: ¿Puedo elegir varios niveles de suscripción para asignarlos dentro de un grupo de Azure AD? 
R: No, todos los miembros del grupo reciben la misma suscripción. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>P: ¿Puedo editar los detalles de suscriptor de los usuarios agregados en un grupo de Azure AD?  
R: No, para modificar la información de un suscriptor individual, deberá quitarlo del grupo de seguridad de Azure AD y asignarle una suscripción individualmente.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>P: He agregado a alguien al grupo de seguridad de Azure AD, pero no lo veo en el Portal de administración de suscripciones ni tiene una suscripción. ¿Por qué no?  
R: En función de cómo haya configurado la organización Azure AD, pueden producirse retrasos de hasta 24 horas antes de que se agregue el usuario. Si han pasado más de 24 horas, [póngase en contacto con el servicio de soporte técnico](https://visualstudio.microsoft.com/support/support-overview-vs).  

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
- ¿Tiene solo que agregar uno o dos suscriptores?  Consulte [Agregar usuarios individuales](assign-license.md).
- ¿Necesita ayuda? Póngase en contacto con el [soporte técnico de administración y suscripciones de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).