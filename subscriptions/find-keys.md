---
title: Búsqueda y reclamación de claves de producto en suscripciones de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: cabuschl
ms.assetid: da8df006-4896-4ff9-b487-698d78deabc3
ms.date: 02/18/2021
ms.topic: conceptual
description: Aprenda a buscar, reclamar y exportar claves de producto en suscripciones de Visual Studio
ms.openlocfilehash: 5e055295e76ee91dbaf641256b8b7e93a530fcfb
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249266"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>Búsqueda y reclamación de claves de producto en suscripciones de Visual Studio
En este artículo se explica cómo buscar, reclamar y exportar claves de producto desde https://my.visualstudio.com/productkeys.  Para obtener más información sobre la activación de un producto con una clave, las versiones de licencia de minorista y por volumen de claves y los límites diarios de reclamación de claves de producto, consulte la [introducción a las claves de producto](product-keys.md).

## <a name="locating-and-claiming-product-keys"></a>Búsqueda y reclamación de claves de producto
Debe iniciar sesión en su suscripción de Visual Studio para ver las claves de producto. Encontrará las claves de producto individuales si selecciona el vínculo azul **Obtener clave** de un determinado producto en la página [Descargas](https://my.visualstudio.com/downloads).  Todas las claves también se encuentran disponibles en la página [Claves de producto](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs). Si hay varias claves para un solo producto, en la columna Notas de la descarga aparecerán unas notas para ayudarle a identificar qué clave se debe usar.
> [!div class="mx-imgBorder"]
> ![Obtención de la clave desde la página Descargas](_img/product-keys/download-get-key.png "Seleccione Obtener clave en la página de información de una descarga a fin de obtener una clave para ese producto.")

A veces se unen varias ediciones del producto en una sola descarga. En estos casos, la clave del producto que se introduce determina la edición del producto que se instalará.
Algunas claves se proporcionan de manera automática, como las claves "estáticas", que puede usar todas las veces necesarias, ya que la activación no es obligatoria. Para reclamar otras claves, seleccione el vínculo **Obtener clave** del producto en cuestión.

Según cuál sea el producto, hay disponibles diversos tipos de clave.

### <a name="product-key-types"></a>Tipos de clave de producto

|    Tipo de clave           |    Descripción                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    No es aplicable                    |    No se requiere clave para instalar este producto.                                                       |
|    Venta directa                     |    Las claves comerciales permiten varias activaciones y se usan para compilaciones minoristas del producto. En muchos casos se permiten 10 activaciones por clave, aunque a menudo se permiten más en el mismo equipo.                                                       |
|    Activación múltiple        |    Una clave de activación múltiple (MAK) le permite activar varias instalaciones de un producto con la misma clave. Por lo general, las MAK se usan con versiones de productos para licencias por volumen. Normalmente, se proporciona una sola clave MAK por suscripción.    |
|    Clave de activación estática    |    Las claves de activación estática se proporcionan para los productos que no necesitan activación. Se pueden usar para un número variado de instalaciones.                                                                                                                  |
|    Clave personalizada                 |    Las claves personalizadas proporcionan acciones o información especial para activar o instalar el producto.                                                                                                                                                                |
|    VA 1.0                     |    Varias claves de activación, similares a MAK.                                                                                                                                                                                                 |
|    Clave OEM                    |    Claves del fabricante de equipo original, que permiten varias activaciones.                                                                                                                                                                       |
|    Clave comercial DreamSpark    |    Claves comerciales para DreamSpark, que permiten solo una activación. Las claves comerciales DreamSpark se emiten por lotes y están pensadas principalmente para los estudiantes.                                                                                     |
|    Clave de laboratorio DreamSpark         |    Claves de uso de laboratorio, para los programas DreamSpark que permiten varias activaciones. Las claves para laboratorio DreamSpark están diseñadas para su uso en escenarios de laboratorios informáticos universitarios.                                                                                       |
|    Clave MAK DreamSpark         |    Claves MAK, para los clientes de programas DreamSpark.                                                                                                                                                                                                  |
|

Puede reclamar una clave en la página de descarga del producto, o bien buscar la clave que necesita en la página [Claves de producto](https://my.visualstudio.com/productkeys).

### <a name="claiming-product-keys"></a>Reclamación de claves de producto
Solo los suscriptores con suscripciones activas pueden descargar productos y reclamar claves de producto.  Puede exportar las claves reclamadas desde la página [Claves de producto](https://my.visualstudio.com/productkeys) mientras su suscripción esté activa.

Para reclamar una clave de producto:
1. Inicie sesión en su suscripción de Visual Studio.  Debe iniciar sesión para descargar productos o reclamar claves de producto.
2. Seleccione la pestaña [Claves de producto](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs).
3. Las claves de producto aparecen ordenadas alfabéticamente por nombre de producto.  Puede ir al nombre del producto que quiera o buscarlo con la barra de búsqueda que hay en la parte superior de la página.
> [!div class="mx-imgBorder"]
> ![Búsqueda de la clave de producto](_img/product-keys/search-keys.png "Desplácese hasta el producto deseado o use el cuadro de búsqueda para localizar rápidamente cualquier producto.")
   
En este ejemplo se ha usado la barra de búsqueda para encontrar una clave de producto de Visual Studio Enterprise 2019.
Como puede ver, aparecen varias versiones.  Una clave ya se ha reclamado para Visual Studio Enterprise 2019 versiones 16.0 y 16.1.  Todavía hay otras claves de tipos diferentes disponibles para ambas versiones. Observe que en la columna **Notas** puede incluir una breve nota sobre las claves reclamadas.  Puede usar esta información con la fecha reflejada en la columna **Reclamado** para llevar un seguimiento de las claves reclamadas.  Por ejemplo, en las notas puede dejar constancia de cuándo ha activado una instalación del producto con la clave.

### <a name="exporting-your-claimed-keys"></a>Exportación de claves reclamadas
Puede exportar una lista de las claves que ha reclamado.  Esto incluye una gran selección de claves estáticas y otras que se marcan automáticamente como "reclamadas".

> [!IMPORTANT]
> Si la suscripción expira, ya no podrá reclamar claves nuevas ni exportar las claves que ya haya reclamado.

Para exportar las claves, seleccione el vínculo **Exportar todas las claves** situado en el extremo derecho de la página Claves de producto.  Se creará un archivo .xml llamado KeysExport.xml y podrá optar entre abrirlo o guardarlo.  Debe abrir el archivo con una aplicación capaz de administrar archivos .xml.  Por ejemplo, puede abrir el archivo como libro de solo lectura en Excel.

## <a name="resources"></a>Recursos
- [Soporte técnico para suscripciones de Visual Studio](https://my.visualstudio.com/gethelp)

## <a name="see-also"></a>Consulte también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Cuando esté listo para descargar software y usar claves, visite https://my.visualstudio.com/downloads.  Para obtener más información sobre la descarga de software, consulte la [introducción a la descarga](download-software.md).