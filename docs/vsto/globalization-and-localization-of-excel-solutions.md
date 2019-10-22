---
title: Globalización y localización de las soluciones de Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b0a7293672bb0b4e74515b71d2e0c4f961440b8c
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255976"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Globalización y localización de las soluciones de Excel
  Esta sección contiene información sobre las consideraciones especiales de las soluciones de Microsoft Office Excel que se vayan a ejecutar en equipos que tengan una configuración de Windows distinta del inglés. La mayoría de los aspectos de globalización y localización de las soluciones de Microsoft Office son los mismos que se pueden encontrar cuando se crean otros tipos de soluciones mediante Visual Studio. Para obtener información general, consulte [globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md).

 De manera predeterminada, los controles de host de Microsoft Office Excel funcionan correctamente en cualquier configuración regional de Windows, siempre y cuando todos los datos que se pasan o manipulan con código administrado tengan el formato correcto de inglés (Estados Unidos). En proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], este comportamiento se controla mediante Common Language Runtime (CLR).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="format-data-in-excel-with-various-regional-settings"></a>Dar formato a los datos en Excel con diversas configuraciones regionales
 Debe formatear todos los datos que tengan un formato dependiente de la configuración regional, como las fechas y la divisa, con el formato de datos de inglés (Estados Unidos) (id. de configuración regional 1033) antes de pasarlos a Microsoft Office Excel o leer los datos desde el código de su proyecto de Office.

 De forma predeterminada, al desarrollar una solución de Office en Visual Studio, el modelo de objetos de Excel espera el formato de datos con id. de configuración regional 1033, lo que se conoce también como bloqueo del modelo de objetos con el id. de configuración regional 1033. Este comportamiento coincide con el modo en que funciona Visual Basic para Aplicaciones. Sin embargo, puede modificar este comportamiento en sus soluciones de Office.

### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>Comprender cómo el modelo de objetos de Excel espera siempre el ID. de configuración regional 1033
 De forma predeterminada, las soluciones de Office que cree con Visual Studio no se ven afectadas por la configuración regional del usuario final y siempre se comportan como si la configuración regional fuera inglés (Estados Unidos). Por ejemplo, si obtiene o establece la propiedad <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> de Excel, los datos deben tener el formato que el id. de configuración regional 1033 espera. Si usa un formato de datos diferente, podría obtener resultados inesperados.

 Incluso aunque use el formato de inglés (Estados Unidos) para los datos que se pasan o manipulan mediante código administrado, Excel interpreta y muestra los datos correctamente según la configuración regional del usuario final. Excel puede aplicar formato correctamente a los datos porque el código administrado pasa el id. de configuración regional 1033 junto con los datos, lo que indica que los datos están en el formato inglés (Estados Unidos) y, por tanto, se debe cambiar el formato para que coincida con la configuración regional del usuario.

 Por ejemplo, si los usuarios finales tienen su configuración regional establecida en la configuración regional de alemán (Alemania), esperan que la fecha 29 de junio de 2005 tenga el formato siguiente: 29.06.2005. Sin embargo, si la solución pasa la fecha a Excel como una cadena, debe dar formato a la fecha según el formato inglés (Estados Unidos): 6/29/2005. Si a la celda se le aplica el formato de celda de fecha, Excel mostrará la fecha en formato de alemán (Alemania).

### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>Pasar otros ID. de configuración regional al modelo de objetos de Excel
 Common Language Runtime (CLR) pasa automáticamente el id. de configuración regional 1033 a todos los métodos y propiedades del modelo de objetos de Excel que aceptan datos que dependen de la configuración regional. No hay ninguna manera de cambiar este comportamiento automáticamente para todas las llamadas al modelo de objetos. Sin embargo, puede pasar un id. de configuración regional diferente a un método específico utilizando <xref:System.Type.InvokeMember%2A> para llamar al método y pasando el id. de configuración regional al parámetro *culture* del método.

## <a name="localize-document-text"></a>Localizar el texto del documento
 El documento, plantilla o libro de su proyecto probablemente incluye texto estático, que se debe localizar por separado del ensamblado y otros recursos administrados. Una manera sencilla de hacerlo es hacer una copia del documento y traducir el texto con Microsoft Office Word o Microsoft Office Excel. Este proceso funciona incluso si no realiza ningún cambio en el código, porque cualquier número de documentos se pueden vincular al mismo ensamblado.

 Aún debe asegurarse de que cualquier parte del código que interactúa con el texto del documento sigue coincidiendo con el idioma del texto y que los marcadores, rangos con nombre y otros campos de visualización se adaptan a cualquier nuevo formato del documento de Office necesario para ajustarse a diferentes gramáticas y longitud de texto. Para plantillas de documentos que contienen relativamente poco texto, es posible que considere la posibilidad de almacenar el texto en archivos de recursos y, a continuación, cargar el texto en tiempo de ejecución.

### <a name="text-direction"></a>Dirección del texto
 En Excel, puede establecer una propiedad de la hoja de cálculo para representar el texto de derecha a izquierda. Los controles host, o cualquier control que tenga `RightToLeft` una propiedad, que se colocan en el diseñador automáticamente coinciden con esta configuración en tiempo de ejecución. Word no tiene una configuración de documento para texto bidireccional (solo tiene que cambiar la alineación del texto), por lo que los controles no se pueden asignar a esta configuración. En su lugar, debe establecer la alineación del texto para cada control. Es posible escribir código para recorrer todos los controles y hacer que representen el texto de derecha a izquierda.

### <a name="change-culture"></a>Cambiar referencia cultural
 Su código de personalización de nivel de documento normalmente comparte el subproceso de la interfaz de usuario principal de Excel, de modo que cualquier cambio que realice a la referencia cultural del subproceso afecta a todo lo demás que se está ejecutando en dicho subproceso; el cambio no se limita a la personalización.

 Los controles de Windows Forms se inicializan antes de que se inicien los complementos de VSTO de nivel de aplicación por la aplicación host. En estas situaciones, se debe cambiar la referencia cultural antes de establecer los controles de la interfaz de usuario.

## <a name="install-the-language-packs"></a>Instalar los paquetes de idioma
 Si tiene una configuración distinta del inglés para Windows, puede instalar los paquetes de idiomas [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para ver los mensajes de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] en el mismo idioma que Windows. Si algún usuario final ejecuta sus soluciones con una configuración distinta del inglés para Windows, deben tener el paquete de idioma correcto para ver los mensajes en tiempo de ejecución en el mismo idioma que Windows. Los [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] paquetes de idioma están disponibles en el [centro de descarga de Microsoft](http://www.microsoft.com/downloads).

 Además, los paquetes de idioma de .NET Framework redistribuibles son necesarios para mensajes de ClickOnce. Los paquetes de idioma de .NET Framework están disponibles en el [centro de descarga de Microsoft](http://www.microsoft.com/downloads).

## <a name="regional-settings-and-excel-com-calls"></a>Configuración regional y llamadas COM de Excel
 Cada vez que un cliente administrado llama a un método en un objeto COM y necesita pasar información específica de la referencia cultural, lo hace mediante <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (configuración regional), que coincide con la configuración regional del subproceso actual. La configuración regional de subproceso actual se hereda de la configuración regional del usuario de manera predeterminada. Sin embargo, al realizar una llamada al modelo de objetos de Excel desde una solución de Excel creada mediante las herramientas de desarrollo de Office en Visual Studio, el formato de datos de inglés (Estados Unidos) (id. de configuración regional 1033) se pasa automáticamente al modelo de objetos de Excel. Debe formatear todos los datos con formato dependiente de la configuración regional, como las fechas y la divisa, con el formato de datos de inglés (Estados Unidos) antes de pasarlos a Microsoft Office Excel o leer los datos desde su código de proyecto.

## <a name="considerations-for-storing-data"></a>Consideraciones para almacenar datos
 Para garantizar que los datos se interpretan y se muestran correctamente, también debe tener en cuenta que se pueden producir problemas cuando una aplicación almacena datos, como fórmulas de hoja de cálculo de Excel, en literales de cadena (codificados de forma rígida) en lugar de en objetos fuertemente tipados. Debe usar datos con un formato que suponga un estilo de referencia cultural invariable o inglés (Estados Unidos) (el valor de LCID 1033).

### <a name="applications-that-use-string-literals"></a>Aplicaciones que usan literales de cadena
 Los valores posibles que podrían estar codificados de forma rígida incluyen literales de fecha escritos en formato inglés (Estados Unidos) y fórmulas de hoja de cálculo de Excel que contengan nombres de función localizados. Otra posibilidad podría ser una cadena codificada de forma rígida que contuviese un número como "1,000"; en algunas referencias culturales, esto se interpreta como mil, pero en otras representa uno coma cero. Los cálculos y las comparaciones llevadas a cabo en el formato incorrecto pueden generar datos incorrectos.

 Excel interpreta las cadenas de acuerdo con el LCID que se pasa con la cadena. Esto puede suponer un problema si el formato de la cadena no se corresponde con el LCID que se pasa. Las soluciones de Excel creadas mediante las herramientas de desarrollo de Office en Visual Studio usan el LCID 1033 (en-US) al pasar todos los datos. Excel muestra los datos según la configuración regional y el idioma de la interfaz de usuario de Excel. Visual Basic para Aplicaciones (VBA) también funciona de esta manera; se da formato a cadenas como en-US y VBA casi siempre pasa 0 (idioma neutral) como el LCID. Por ejemplo, el siguiente código VBA muestra un valor con formato correcto para el 12 de mayo de 2004, de acuerdo con la configuración regional del usuario actual:

```vb
'VBA
Application.ActiveCell.Value2 = "05/12/04"
```

 El mismo código, cuando se usa en una solución creada mediante las herramientas de desarrollo de Office en Visual Studio y se pasa a Excel a través de interoperabilidad COM, genera los mismos resultados cuando la fecha tiene el formato de estilo de en-US.

 Por ejemplo:

 [!code-vb[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#6)]
 [!code-csharp[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#6)]

 Debe trabajar con datos fuertemente tipados en lugar de literales de cadena siempre que sea posible. Por ejemplo, en lugar de almacenar una fecha en un literal de cadena, almacénela como <xref:System.Double>y luego conviértala en un objeto <xref:System.DateTime> para la manipulación.

 En el ejemplo de código siguiente se toma una fecha que un usuario escribe en la celda A5, se almacena como <xref:System.Double>y luego se convierte en un objeto <xref:System.DateTime> para mostrarlo en la celda A7. La celda A7 debe tener el formato para mostrar una fecha.

 [!code-vb[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#7)]
 [!code-csharp[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#7)]

### <a name="excel-worksheet-functions"></a>Funciones de hoja de cálculo de Excel
 Los nombres de función de hoja de cálculo se traducen internamente para la mayoría de las versiones de idioma de Excel. Sin embargo, debido a posibles problemas de interoperabilidad COM y de lenguaje, se recomienda usar solo nombres de función en inglés en el código.

### <a name="applications-that-use-external-data"></a>Aplicaciones que usan datos externos
 Cualquier código que abre o que usa de otra manera datos externos, como los archivos que incluyen valores separados por comas (archivos CSV) exportados desde un sistema heredado, también podrían verse afectados si se exportan tales archivos con cualquier formato distinto de en-US. Es posible que el acceso a los datos no se vea afectado porque todos los valores deberían estar en formato binario, a menos que la base de datos almacene fechas como cadenas o realice operaciones que no usan formato binario. Además, si crea consultas SQL con datos de Excel, es posible que tenga que garantizar que están en formato en-US, según la función que use.

## <a name="see-also"></a>Vea también

- [Cómo: Destino de la interfaz de usuario multilingüe de Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)