---
title: Diseñador de flujo de trabajo - Diseñador de actividades TryCatch
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 280f844ec08ea5e75a78d2e9ea1596b0fb7162eb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859008"
---
# <a name="trycatch-activity-designer"></a>Diseñador de actividades TryCatch

El **TryCatch** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.TryCatch> actividad.

## <a name="the-trycatch-activity"></a>Actividad TryCatch
 El <xref:System.Activities.Statements.TryCatch> actividad contiene una <xref:System.Activities.Statements.TryCatch.Try%2A> actividad, una colección de **Catch\<TException >** y un <xref:System.Activities.Statements.TryCatch.Finally%2A> actividad. Un <xref:System.Activities.Statements.Catch%601> typu **TException** contiene un <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> y un <xref:System.Activities.Statements.Catch%601.Action%2A>. Todas ellas se utilizan para implementar un mecanismo típico de control de errores basado en excepciones. Una actividad <xref:System.Activities.Statements.TryCatch> intenta ejecutar su actividad <xref:System.Activities.Statements.TryCatch.Try%2A>. Si el <xref:System.Activities.Statements.TryCatch.Try%2A> actividad produce una excepción, el <xref:System.Activities.Statements.TryCatch> actividad usa su **Catch < TException\>**  colección para que coincida con la excepción. Si hay una coincidencia, el <xref:System.Activities.Statements.Catch%601.Action%2A> de correspondiente **Catch\<TException >** se ejecuta, que actúa como la lógica para la excepción de control de errores. Si las actividades de la sección <xref:System.Activities.Statements.TryCatch.Try%2A> se completan correctamente o las actividades de <xref:System.Activities.Statements.TryCatch.Catches%2A> se completan correctamente, la actividad <xref:System.Activities.Statements.TryCatch> ejecuta su actividad <xref:System.Activities.Statements.TryCatch.Finally%2A>. Para obtener más información, consulte [excepciones de flujo de trabajo de Windows](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Utilizar el diseñador de actividades TryCatch

Acceso a la **TryCatch** Diseñador de actividad en el **control de errores** categoría de la **cuadro de herramientas**.

El **TryCatch** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Esto crea una actividad <xref:System.Activities.Statements.TryCatch> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de TryCatch. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado de la **TryCatch** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades. Las demás propiedades se deben editar en la superficie de la **TryCatch** Diseñador de actividad.

Haga clic en el botón de expansión en la esquina superior derecha de **TryCatch** diseñador para ver el **intente**, **detecta**, y **finalmente** cuadros en el vista expandida. Para agregar un bloque catch, haga clic en el **agregar nueva instrucción catch** situado en **TryCatch** diseñador. El botón cambia a un cuadro combinado de tipo. Seleccione un tipo de excepción y presione ENTRAR para agregar la instrucción catch. Después de agregar un **Catch**, el área de catch se expande y se puede colocar una actividad en la instrucción catch para definir la lógica de ejecución para la captura. Observe que hay un cuadro de texto a la derecha del área de la instrucción catch expandida. Puede asignar un nombre a la variable de excepción con este cuadro de texto. La variable de excepción sólo puede utilizarse para las actividades dentro de la misma **Catch**.

El **TryCatch** diseñador no admite la edición **Catch**. Si desea cambiar el tipo de excepción, tiene que eliminar el **Catch** y agregar uno nuevo. Un **Catch** pueden eliminarse, selecciónela y eliminarla o mediante el **eliminar** menú en el menú contextual que se puede obtener acceso a la derecha haciendo.

### <a name="the-trycatch-properties"></a>Propiedades TryCatch

La tabla siguiente muestra la <xref:System.Activities.Statements.TryCatch>propiedades y se describe cómo se usan en el diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.TryCatch>. El valor predeterminado es TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|La actividad se ejecuta primero cuando <xref:System.Activities.Statements.TryCatch> se ejecuta.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|La colección de **Catch** los elementos que se va a comprobar cuando la <xref:System.Activities.Statements.TryCatch.Try%2A> actividad produce una excepción.<br /><br /> Necesita agregar al menos una actividad en <xref:System.Activities.Statements.TryCatch.Catches%2A> o en el bloque <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|La actividad que se va a ejecutar cuando la clase <xref:System.Activities.Statements.TryCatch.Try%2A> y cualquiera de las actividades necesarias en la colección <xref:System.Activities.Statements.TryCatch.Catches%2A> completen la ejecución.<br /><br /> Necesita agregar al menos una actividad en <xref:System.Activities.Statements.TryCatch.Catches%2A> o en el bloque <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)