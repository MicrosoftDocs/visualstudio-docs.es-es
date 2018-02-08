---
title: "Administración de derechos de administrador en el Portal de administrador de suscripciones de Visual Studio"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/19/2018
Ms.topic: Get-Started-Article
Description: Learn how manage admins & super admins in the Visual Studio Subscriptions Administrator Portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 83bf27d5aaa99c2095ad8a1fafd7541df90f316b
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="managing-administrator-rights-in-the-visual-studio-subscriptions-administrator-portal"></a>Administración de derechos de administrador en el Portal de administrador de suscripciones de Visual Studio

## <a name="overview"></a>Información general 
En el Portal de administrador de suscripciones de Visual Studio (https://manage.visualstudio.com) existen dos roles:

**Superadministradores:** al configurar una organización por primera vez, el contacto principal o el encargado de los avisos es de forma predeterminada el superadministrador. El contacto principal o el encargado de los avisos puede asignar superadministradores o administradores adicionales. Además de administrar las suscripciones de los suscriptores individuales, los superadministradores pueden agregar y quitar otros administradores y superadministradores. Si hay más de dos superadministradores en el sistema, un superadministrador puede eliminarlos a todos menos a los dos últimos por razones de seguridad. 

**Administradores:** un administrador puede administrar los suscriptores de los contratos que el superadministrador le asigne.  Puede asignar suscripciones a usuarios individuales, editar las suscripciones y reasignarlas o quitarlas   (los administradores son designados por los superadministradores).  

## <a name="adding-an-administrator-with-super-admin-rights"></a>Adición de un administrador **con** derechos de superadministrador:

1. Inicie sesión en el [Portal de administrador](https://manage.visualstudio.com) de suscripciones de Visual Studio con una cuenta que ya tenga derechos de superadministrador.

2. Haga clic en la pestaña **Administrar administradores** de la parte superior de la página. (Solo los superadministradores tienen acceso a esta pestaña.  Los administradores sin derechos de superadministrador utilizan la pestaña **Administrar administradores** para administrar suscriptores individuales).

3. Haga clic en **Agregar** para crear un nuevo administrador. 

4. Rellene todos los detalles solicitados en la ventana emergente Agregar administrador.
  - Si su organización ya se ha inscrito en Azure Active Directory (AAD), comience a escribir el nombre en el campo **Nombre** y seleccione el elemento correspondiente en la lista desplegable. Con nuevos usuarios, escriba el nombre completo y omita la notificación *No se encontraron identidades*.
  - Una vez identificado el usuario correcto, se rellenará automáticamente el campo Dirección de correo electrónico de inicio de sesión. Escriba la dirección de correo electrónico del administrador nuevo, si aún no la ha proporcionado.

5. Seleccione el **PCN** (número de cliente público) que desea que administre el nuevo administrador; para ello, haga clic en la lista desplegable bajo **Contratos**. Si el PCN que está agregando tiene más de un contrato, puede proporcionar acceso al administrador a cualquiera de ellos o a todos. 

**Más información sobre contratos:** la funcionalidad desplegable bajo Contratos se deshabilita cuando hay solo un contrato disponible.  Todos los contratos se activan automáticamente cuando al usuario que está configurando se le conceden derechos de superadministrador.

6. Haga clic en el cuadro **Superadministrador** para habilitar los derechos de superadministrador para este administrador.  

7. Para terminar de agregar este administrador, haga clic en **Agregar**.

**Posible error recibido al agregar administradores:** algunos usuarios pueden recibir un mensaje de error al intentar agregar al administrador. Esto es probable que ocurra si la dirección de correo electrónico del superadministrador que se está agregando no figura en el directorio AAD de la empresa. Para terminar de agregar al nuevo administrador, basta con pasar por alto el error y hacer clic en **Agregar** de nuevo. 

8. Una vez creado un superadministrador, podrá verlo en la lista de administradores, y su cuenta se señalará con una marca de verificación verde para indicar su estado de superadministrador. 

### <a name="optional--add-a-different-notification-email"></a>Opcional: adición de un correo electrónico de notificación diferente.
Si su organización tiene una dirección o cuenta diferente para recibir correos electrónicos, ahora tiene la opción de especificar una dirección de "Comunicación". Seleccione **Add a different notification email for receiving communication** (Agregar un correo electrónico de notificación diferente para recibir comunicaciones). 

*Ejemplo:* Tomás usa rene@contoso.com cuando inicia sesión con sus credenciales de empresa.  Sin embargo, la empresa de Tomás solo usa esa dirección para administrar el acceso al directorio.  Al enviar y recibir mensajes de correo electrónico, Tomás usa rene.collado@contoso.com, por lo que su superadministrador ha especificado una segunda dirección para asegurarse de que recibe los correos electrónicos de bienvenida.  Si su empresa no está configurada de esta manera, debería bastar con escribir la dirección de correo electrónico de inicio de sesión.

## <a name="adding-an-administrator-without-super-admin-rights"></a>Adición de un administrador **sin** derechos de superadministrador:

Debe seguirse el mismo proceso tal y como se ha descrito anteriormente para agregar administradores sin derechos de superadministrador, pero teniendo en cuenta los siguientes aspectos:
-  Al agregar administradores sin derechos de superadministrador, no es necesario especificar una dirección de correo electrónico adicional, y la casilla Superadministrador se queda en blanco.
-  Los usuarios sin derechos de superadministrador no reciben el icono de marca de verificación verde en su entrada de configuración de perfil en "Administrar administradores".
