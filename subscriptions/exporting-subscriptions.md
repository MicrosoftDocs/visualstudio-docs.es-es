---
title: Exportar la información de suscripción | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/14/2018
ms.topic: conceptual
description: Obtenga información sobre cómo exportar una lista de suscriptores y los detalles de sus asignaciones de suscripciones.
searchscope: VS Subscription
ms.openlocfilehash: 7e2db1c0de036441801aa56ae1956d0a10719798
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844034"
---
# <a name="exporting-subscription-information"></a>Exportar la información de suscripción

En el [portal del administrador](https://manage.visualstudio.com) de suscripciones de Visual Studio, puede exportar una lista de los usuarios y los detalles de sus asignaciones. Esta información incluye su nombre, dirección de correo electrónico, dirección de correo electrónico alternativa, nivel de suscripción, fecha asignada, estado de activación, fecha de expiración, campo de referencia, descargas habilitadas, país, idioma, estado de la suscripción y GUID de la suscripción.

Esta característica es útil para algunos escenarios, como el seguimiento de las asignaciones y las fechas de expiración. Si, por ejemplo, está cambiando la manera de realizar el seguimiento de las suscripciones para usar GUID en lugar de BAN, puede usar este informe con la fórmula VLOOKUP en Microsoft Excel para que coincida con los suscriptores de forma adecuada.

Para realizar la exportación, simplemente seleccione la pestaña **Exportar** y el archivo se descargará en el equipo local. El archivo incluirá el nombre del acuerdo que contiene las suscripciones de los usuarios, así como la fecha de la exportación.
> [!div class="mx-imgBorder"]
> ![Exportar suscriptores](_img/exporting-subscriptions/exporting-subscriptions.png)
