---
title: Diseño de aplicaciones de Windows Forms
description: Obtenga información sobre el Diseñador de Windows Forms de Visual Studio, que brinda una solución de desarrollo rápida para crear aplicaciones basadas en Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: overview
helpviewer_keywords:
- Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 768c19f78102bf19346867beda967a069c1d182e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844962"
---
# <a name="windows-forms-designer-overview"></a>Información general del Diseñador de Windows Forms

El Diseñador de Windows Forms de Visual Studio brinda una solución de desarrollo rápida para crear aplicaciones basadas en Windows Forms. El Diseñador de Windows Forms le permite agregar fácilmente controles a un formulario, organizarlos y escribir código para sus eventos. Para más información sobre Windows Forms, consulte la [información general sobre Windows Forms](/dotnet/framework/winforms/windows-forms-overview).

## <a name="functionality"></a>Funcionalidad

Con el diseñador es posible:

- Agregar a un formulario componentes, controles de datos o controles basados en Windows.

- Hacer doble clic en el formulario en el diseñador y escribir código en el evento `Load` para ese formulario, o bien hacer doble clic en un control del formulario y escribir código para el evento predeterminado del control.

- Editar la propiedad Text de un control al seleccionar el control y escribir un nombre.

- Ajustar la posición del control seleccionado al moverlo con el mouse o con las teclas de dirección. Del mismo modo, es posible ajustar la ubicación de manera más precisa con las teclas de dirección y Ctrl. Por último, se puede ajustar el tamaño del control con las teclas de dirección y Mayús.

- Seleccionar varios controles al seleccionar **Mayús** o **Ctrl** mientras se hace clic. Cuando se usa **Mayús**+clic, el primer control seleccionado es el dominante al alinear o manipular el tamaño. Cuando se usa **Ctrl**+clic, el último control seleccionado es el dominante, por lo que el control dominante cambia cada vez que se agrega un control. De manera alternativa, puede seleccionar varios controles si arrastra un rectángulo de selección alrededor de los controles que quiere seleccionar.

> [!NOTE]
> Use el Diseñador de Windows Forms, no el Editor de recursos, para modificar el archivo de recursos (*.resx*) de un formulario. Si edita un archivo .resx basado en formulario, verá una advertencia que indica que es posible que se pierdan los cambios que haga en el Editor de recursos. Esto se debe a que el Diseñador de Windows Forms genera el archivo .resx.

## <a name="see-also"></a>Consulte también

- [Información general sobre Windows Forms](/dotnet/framework/winforms/windows-forms-overview)
- [Controles de Windows Forms](/dotnet/framework/winforms/controls/)
- [Datos proporcionados por el usuario en Windows Forms](/dotnet/framework/winforms/user-input-in-windows-forms)
- [Enlace de datos en Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding)
- [Mejoramiento de las aplicaciones de Windows Forms](/dotnet/framework/winforms/advanced/)
- Referencia de API <xref:System.Windows.Forms?displayProperty=fullName>
