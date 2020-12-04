---
title: ¿Cómo se asignan las suscripciones de Visual Studio?
description: Puede asignar suscripciones a los usuarios finales de una en una, o bien usar la característica Agregar en masa para cargar de forma rápida y sencilla un mayor...
ms.faqid: group1_3
ms.topic: include
ms.assetid: 59eb35fd-ec94-41ce-b24c-a8a120976bac
author: CaityBuschlen
ms.author: cabuschl
ms.date: 12/03/2020
ms.openlocfilehash: 5a12d59f90ee2a09002efcb99c78cfd563060006
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2020
ms.locfileid: "96584566"
---
## <a name="how-do-i-assign-visual-studio-subscriptions"></a>¿Cómo se asignan las suscripciones de Visual Studio?

Puede asignar suscripciones a los usuarios finales de una en una, o bien usar la característica Agregar en masa para cargar de forma rápida y sencilla un mayor número de suscriptores a la vez.

Para asignar las suscripciones de forma individual:

1. Seleccione la pestaña [Administrar suscriptores](https://manage.visualstudio.com/subscribers) de la parte superior de la página en [manage.visualstudio.com](https://manage.visualstudio.com).
2. Seleccione Agregar y escriba el nombre y la dirección de correo electrónico del usuario al que le gustaría asignar una suscripción.
    1. Si en la organización se usa Azure Active Directory, el campo Nombre buscará usuarios en el directorio actual. Puede seleccionar en los resultados de la búsqueda, o bien agregar un usuario de forma manual.
3. Si quiere que el suscriptor tenga acceso a las descargas de software cuando inicie sesión en el [portal de suscripciones de Visual Studio](https://my.visualstudio.com/), asegúrese de dejar habilitadas las descargas en la sección Configuración de descarga.
4. Complete la sección Preferencias de comunicación para que sepamos en qué idioma se debe enviar el correo electrónico de asignación a los suscriptores.
5. Si quiere agregar notas asociadas en la asignación, use la selección de referencias.
6. Seleccione Agregar en la parte inferior del panel emergente para completar la asignación de la suscripción. El suscriptor recibirá un correo electrónico y podrá empezar a usar inmediatamente su suscripción de Visual Studio (no tiene que realizar ninguna activación).

Para asignar suscripciones en masa:

1. Seleccione la pestaña [Administrar suscriptores](https://manage.visualstudio.com/subscribers) de la parte superior de la página en [manage.visualstudio.com](https://manage.visualstudio.com).
2. Seleccione Agregar en masa, descargue la plantilla de Excel y guarde una copia local.
3. Todos los campos son obligatorios, menos Referencia.
    1. Asegúrese de que ninguno de los campos del formulario contiene comas.
    2. Quite los espacios de delante y detrás de los campos del formulario.
    3. Asegúrese de que los nombres no contienen espacios adicionales entre las dos partes de los nombres o apellidos compuestos (por ejemplo, si un usuario tiene el nombre compuesto "Maggie May", se debe escribir como "MaggieMay").
4. Vuelva a [manage.visualstudio.com](https://manage.visualstudio.com), seleccione Agregar en masa y cargue la copia guardada de la plantilla de Excel.
5. Cuando la carga se realice correctamente, verá una página de confirmación y la lista de suscriptores se rellenará con los nuevos suscriptores. Los suscriptores recibirán un correo electrónico y podrán empezar a usar inmediatamente su suscripción de Visual Studio (no tienen que realizar ninguna activación).

[Obtenga más información](https://docs.microsoft.com/visualstudio/subscriptions/assign-license#add-a-single-subscriber) sobre la asignación de suscripciones en el portal de administrador de suscripciones de Visual Studio para saber más sobre cómo asignar suscripciones de forma rápida y sencilla.  Obtenga [más información](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) sobre la administración de suscripciones de Visual Studio con GitHub Enterprise. 

## <a name="what-is-the-github-enterprise-setup-process"></a>¿Qué es el proceso de configuración de GitHub Enterprise? 

GitHub Enterprise se configura y se administra de forma independiente de las suscripciones de Visual Studio. Tras una compra de una suscripción a Visual Studio con GitHub Enterprise, se inicia un proceso de configuración de cuenta de GitHub Enterprise en paralelo al establecimiento de un contrato en manage.visualstudio.com, pero de forma independiente a este. El establecimiento de esta cuenta de GitHub Enterprise puede tardar un tiempo.  

Una vez que la empresa ha configurado una cuenta de GitHub Enterprise, los suscriptores a los que se les hayan asignado suscripciones de Visual Studio con GitHub Enterprise recibirán un correo electrónico de GitHub en el que se les notificará que sus suscripciones de Visual Studio se han vinculado. Después de que los suscriptores reciban este correo electrónico, podrán ponerse en contacto con el administrador de la organización de GitHub para recibir una invitación a la organización adecuada. 

[Obtenga más información](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) sobre cómo administrar suscripciones de Visual Studio con GitHub Enterprise. Consulte la [documentación del suscriptor](https://docs.microsoft.com/visualstudio/subscriptions/access-github) para obtener más detalles sobre el proceso de configuración de GitHub Enterprise. 