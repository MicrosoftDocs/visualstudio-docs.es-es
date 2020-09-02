---
title: Combinar personalizaciones de VBA y de nivel de documento
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b3bab9c132439c6efa53842f1e13c6c5be31db00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "70977597"
---
# <a name="combine-vba-and-document-level-customizations"></a>Combinar personalizaciones de VBA y de nivel de documento
  Puede utilizar código de Visual Basic para Aplicaciones (VBA) en un documento que forme parte de una personalización de nivel de documento de Microsoft Office Word o Microsoft Office Excel. Puede llamar a código VBA del documento desde el ensamblado de personalización o puede configurar el proyecto de modo que permita que el código VBA del documento llame a código del ensamblado de personalización.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Comportamiento del código VBA en una personalización de nivel de documento
 Al abrir el proyecto en Visual Studio, el documento se abre en modo de diseño. El código VBA no se ejecuta si el documento está en modo de diseño, así que puede trabajar en el documento y el código sin ejecutar el código VBA.

 Al ejecutar la solución, los controladores de eventos de VBA y el ensamblado de personalización recopilan los eventos que se producen en el documento y ambos conjuntos de código se ejecutan. No se puede determinar de antemano qué código se ejecutará antes que el otro; se debe determinar mediante pruebas en cada caso individual. Puede obtener resultados inesperados si los dos conjuntos de código no se han coordinado y probado cuidadosamente.

## <a name="call-vba-code-from-the-customization-assembly"></a>Llamar a código VBA desde el ensamblado de personalización
 Puede llamar a macros en documentos de Word y a funciones y macros en libros de Excel. Para ello, use uno de los siguientes métodos:

- En Word, llame al <xref:Microsoft.Office.Interop.Word._Application.Run%2A> método de la <xref:Microsoft.Office.Interop.Word.Application> clase.

- En Excel, llame al método <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> de la clase <xref:Microsoft.Office.Interop.Excel.Application> .

  En cada método, el primer parámetro identifica al nombre de la macro o función a la que desea llamar; los parámetros opcionales restantes especifican los parámetros que se van a pasar a la macro o función. El primer parámetro puede tener formatos diferentes para Word y Excel:

- En Word, el primer parámetro es una cadena que puede ser cualquier combinación de nombre de plantilla, módulo y macro. Si especifica el nombre del documento, el código solo puede ejecutar macros en documentos relacionados con el contexto actual, no cualquier macro en cualquier documento.

- En Excel, el primer parámetro puede ser una cadena que especifique el nombre de la macro, un <xref:Microsoft.Office.Interop.Excel.Range> que indique dónde está la función o un identificador de registro de una función DLL (XLL) registrada. Si pasa una cadena, esta se evaluará en el contexto de la hoja activa.

  En el ejemplo de código siguiente se muestra cómo llamar a una macro denominada `MyMacro` desde un proyecto de nivel de documento para Excel. En este ejemplo se da por supuesto que `MyMacro` se define en `Sheet1`.

```vb
Globals.Sheet1.Application.Run("MyMacro")
```

```csharp
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing);
```

> [!NOTE]
> Para obtener información sobre cómo usar la `missing` variable global en lugar de los parámetros opcionales en Visual C#, vea [escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md).

## <a name="call-code-in-document-level-customizations-from-vba"></a>Llamar a código en personalizaciones de nivel de documento desde VBA
 Puede configurar un proyecto de nivel de documento para Word o Excel de modo que código de Visual Basic para Aplicaciones (VBA) del documento pueda llamar a código del ensamblado de personalización. Esto es útil en los siguientes escenarios:

- Desea ampliar el código VBA existente en un documento mediante las características de una personalización de nivel de documento que está asociada con el mismo documento.

- Desea que los servicios que desarrolla en una personalización de nivel de documento estén disponibles para los usuarios finales que pueden obtener acceso a los servicios al escribir código VBA en el documento.

  Las herramientas de desarrollo de Office en Visual Studio proporcionan una característica similar para los complementos de VSTO. Si está desarrollando un complemento de VSTO, puede llamar a código en el complemento de VSTO desde otras soluciones de Microsoft Office. Para obtener más información, consulte [llamar a código en complementos de VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

> [!NOTE]
> Esta característica no se puede utilizar en proyectos de plantilla de Word. Se puede usar únicamente en proyectos de plantilla de Excel, libro de Excel o documento de Word.

## <a name="requirements"></a>Requisitos
 Para habilitar código VBA para llamar al ensamblado de personalización, el proyecto debe cumplir los siguientes requisitos:

- El documento debe tener una de las siguientes extensiones de nombre de archivo:

  - En Word: *. docm* o *. doc*

  - Para Excel: *. xlsm*, *. xltm*, *. xls*o *. xlt*

- El documento ya debe contener un proyecto de VBA con código VBA.

- Se debe permitir que el código VBA del documento se ejecute sin pedir al usuario que habilite macros. Puede confiar en la ejecución de código VBA si agrega la ubicación del proyecto de Office a la lista de ubicaciones de confianza en la configuración del Centro de confianza de Word o Excel.

- El proyecto de Office debe contener al menos una clase pública que contenga uno o más miembros públicos que esté exponiendo a VBA.

     Puede exponer métodos, propiedades y eventos a VBA. La clase que exponga puede ser una clase de elemento host (como `ThisDocument` para Word o `ThisWorkbook` y `Sheet1` para Excel) u otra clase que defina en el proyecto. Para obtener más información sobre los elementos host, vea [información general sobre elementos y controles](../vsto/host-items-and-host-controls-overview.md)host.

## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>Habilitar código VBA para llamar al ensamblado de personalización
 Hay dos maneras diferentes de exponer a los miembros de un ensamblado de personalización a código VBA en el documento:

- Puede exponer a los miembros de una clase de elemento host de un proyecto de [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] a VBA. Para ello, establezca la propiedad **EnableVbaCallers** del elemento host en **True** en la ventana **Propiedades** mientras el elemento host (es decir, el documento, la hoja de cálculo o el libro) está abierto en el diseñador. Visual Studio realiza automáticamente todo el trabajo necesario para permitir que el código VBA llame a los miembros de la clase.

- Puede exponer a los miembros de cualquier clase pública de un proyecto de Visual C# o a los miembros de una clase de elemento no hospedada de un proyecto de [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] a VBA. Esta opción le da más libertad para elegir qué clases expone a VBA, pero también exige más pasos manuales.

   Para ello, debe realizar los pasos principales siguientes:

  1. Exponer la clase a COM.

  2. Reemplazar el método **GetAutomationObject** de una clase de elemento host del proyecto para devolver una instancia de la clase que está exponiendo a VBA.

  3. Establecer la propiedad **ReferenceAssemblyFromVbaProject** de cualquier clase de elemento host del proyecto en **True**. Esto incrusta la biblioteca de tipos del ensamblado de personalización en el ensamblado y agrega una referencia a la biblioteca de tipos al proyecto de VBA del documento.

  Para obtener instrucciones detalladas, vea [Cómo: exponer código a VBA en un proyecto de Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) y [Cómo: exponer código a VBA en un proyecto de&#35; de Visual C](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

  Las propiedades **EnableVbaCallers** y **ReferenceAssemblyFromVbaProject** solo están disponibles en la ventana **Propiedades** en tiempo de diseño; no se pueden utilizar en tiempo de ejecución. Para ver las propiedades, abra el diseñador de un elemento host en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información sobre las tareas específicas que Visual Studio realiza cuando se establecen estas propiedades, vea [tareas realizadas por las propiedades del elemento host](#PropertyTasks).

> [!NOTE]
> Si el documento o libro aún no contiene código VBA o si el código VBA del documento no es de confianza para ejecutar, recibirá un mensaje de error al establecer la propiedad **EnableVbaCallers** o **ReferenceAssemblyFromVbaProject** en **True**. Esto se debe a que Visual Studio no puede modificar el proyecto de VBA del documento en esta situación.

## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>Usar miembros en código VBA para llamar al ensamblado de personalización
 Después de configurar el proyecto para que el código VBA pueda llamar al ensamblado de personalización, Visual Studio agrega los miembros siguientes al proyecto de VBA del documento:

- Para todos los proyectos, Visual Studio agrega un método global denominado `GetManagedClass`.

- En el caso de los [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] proyectos en los que se exponen miembros de una clase de elemento host mediante la propiedad **EnableVbaCallers** , Visual Studio también agrega una propiedad denominada `CallVSTOAssembly` al `ThisDocument` `ThisWorkbook` módulo,,, o del `Sheet1` `Sheet2` `Sheet3` proyecto de VBA.

  Puede utilizar la propiedad `CallVSTOAssembly` o el método `GetManagedClass` para tener acceso a los miembros públicos de la clase que expuso a código VBA en el proyecto.

> [!NOTE]
> Mientras desarrolla e implementa la solución, hay varias copias diferentes del documento donde puede agregar el código VBA. Para obtener más información, vea [directrices para agregar código VBA al documento](#Guidelines).

### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Uso de la propiedad CallVSTOAssembly en un proyecto de Visual Basic
 Utilice la propiedad `CallVSTOAssembly` para tener acceso a los miembros públicos que agregó a la clase de elemento host. Por ejemplo, la siguiente macro VBA llama a un método denominado `MyVSTOMethod` que se define en la clase `Sheet1` de un proyecto de libro de Excel.

```vb
Sub MyMacro()
    Sheet1.CallVSTOAssembly.MyVSTOMethod()
End Sub
```

 Esta propiedad es una manera más conveniente de llamar al ensamblado de personalización que el uso del método `GetManagedClass` directamente. `CallVSTOAssembly` devuelve un objeto que representa a la clase de elemento host que expuso a VBA. Los miembros y los parámetros de método del objeto devuelto aparecen en IntelliSense.

 La propiedad `CallVSTOAssembly` tiene una declaración similar al código siguiente. Este código supone que ha expuesto la clase de elemento host `Sheet1` de un proyecto de libro de Excel denominado `ExcelWorkbook1` a VBA.

```vb
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1
    Set CallVSTOAssembly = GetManagedClass(Me)
End Property
```

### <a name="use-the-getmanagedclass-method"></a>Usar el método GetManagedClass
 Para usar el método global `GetManagedClass` , pase el objeto VBA que corresponde a la clase de elemento host que contiene el reemplazo del método **GetAutomationObject** . A continuación, utilice el objeto devuelto para obtener acceso a la clase que expuso a VBA.

 Por ejemplo, la siguiente macro VBA llama a un método denominado `MyVSTOMethod` que se define en la clase de elemento host `Sheet1` de un proyecto de libro de Excel llamado `ExcelWorkbook1`.

```vb
Sub CallVSTOMethod
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1
    Set VSTOSheet1 = GetManagedClass(Sheet1)
    VSTOSheet1.MyVSTOMethod
End Sub
```

 El método `GetManagedClass` tiene la siguiente declaración.

```vb
GetManagedClass(pdispInteropObject Object) As Object
```

 Este método devuelve un objeto que representa a la clase que expuso a VBA. Los miembros y los parámetros de método del objeto devuelto aparecen en IntelliSense.

## <a name="guidelines-for-adding-vba-code-to-the-document"></a><a name="Guidelines"></a> Directrices para agregar código VBA al documento
 Hay varias copias diferentes del documento donde puede agregar código VBA que llama a la personalización de nivel de documento.

 A medida que desarrolla y prueba la solución, puede escribir código VBA en el documento que se abre mientras depura o ejecuta el proyecto en Visual Studio (es decir, el documento de la carpeta de resultados de compilación). Sin embargo, cualquier código VBA que agregue a este documento se sobrescribirá la siguiente vez que compile el proyecto, ya que Visual Studio reemplaza el documento de la carpeta de resultados de compilación por una copia del documento de la carpeta de proyecto principal.

 Si desea guardar el código VBA que agregue al documento mientras depura o ejecuta la solución, copie el código VBA en el documento de la carpeta de proyecto. Para obtener más información sobre el proceso de compilación, vea [compilar soluciones de Office](../vsto/building-office-solutions.md).

 Cuando esté listo para implementar la solución, hay tres ubicaciones principales del documento en las que puede agregar el código VBA.

### <a name="in-the-project-folder-on-the-development-computer"></a>En la carpeta del proyecto en el equipo de desarrollo
 Esta ubicación es conveniente si tiene un control completo sobre el código VBA del documento y el código de personalización. Dado que el documento se encuentra en el equipo de desarrollo, puede modificar fácilmente el código VBA si cambia el código de personalización. El código VBA que agregue a esta copia del documento permanece en el documento al compilar, depurar y publicar la solución.

 No se puede agregar el código VBA al documento mientras está abierto en el diseñador. Primero debe cerrar el documento en el diseñador y, a continuación, abrirlo directamente en Word o Excel.

> [!CAUTION]
> Si agrega código VBA que se ejecuta al abrir el documento, en ciertas ocasiones este código podría dañar el documento o evitar que se abriera en el diseñador.

### <a name="in-the-publish-or-installation-folder"></a>En la carpeta de publicación o instalación
 En algunos casos, podría ser conveniente agregar el código VBA al documento en la carpeta de instalación o publicación. Por ejemplo, puede elegir esta opción si el código VBA ha sido escrito y probado por un otro desarrollador en un equipo que no tiene instalado Visual Studio.

 Si los usuarios instalan la solución directamente desde la carpeta de publicación, debe agregar el código VBA al documento cada vez que publique la solución. Visual Studio sobrescribe el documento de la ubicación de publicación cuando se publica la solución.

 Si los usuarios instalan la solución desde una carpeta de instalación distinta a la carpeta de publicación, puede evitar tener que agregar el código VBA en el documento cada vez que publique la solución. Cuando haya una actualización de publicación lista para moverse de la carpeta de publicación a la carpeta de instalación, copie todos los archivos en la carpeta de instalación, salvo el documento.

### <a name="on-the-end-user-computer"></a>En el equipo del usuario final
 Si los usuarios finales son desarrolladores de VBA que llaman a los servicios que proporciona en la personalización de nivel de documento, puede indicarles cómo llamar al código mediante la propiedad `CallVSTOAssembly` o el método `GetManagedClass` de sus copias del documento. Al publicar actualizaciones en la solución, el código VBA del documento del equipo del usuario final no se sobrescribirá, porque las actualizaciones de publicación no modifican el documento.

## <a name="tasks-performed-by-the-host-item-properties"></a><a name="PropertyTasks"></a> Tareas realizadas por las propiedades del elemento host
 Cuando se usan las propiedades **EnableVbaCallers** y **ReferenceAssemblyFromVbaProject** , Visual Studio realiza diferentes conjuntos de tareas.

### <a name="enablevbacallers"></a>EnableVbaCallers
 Al establecer la propiedad **EnableVbaCallers** de un elemento host en **True** en un proyecto de Visual Basic, Visual Studio realiza las siguientes tareas:

1. Agrega los atributos <xref:Microsoft.VisualBasic.ComClassAttribute> y <xref:System.Runtime.InteropServices.ComVisibleAttribute> a la clase de elemento host.

2. Reemplaza el método **GetAutomationObject** de la clase de elemento host.

3. Establece la propiedad **ReferenceAssemblyFromVbaProject** del elemento host en **True**.

   Al volver a establecer la propiedad **EnableVbaCallers** en **False**, Visual Studio realiza las siguientes tareas:

4. Quita los atributos <xref:Microsoft.VisualBasic.ComClassAttribute> y <xref:System.Runtime.InteropServices.ComVisibleAttribute> de la clase `ThisDocument` .

5. Quita el método **GetAutomationObject** de la clase de elemento host.

   > [!NOTE]
   > Visual Studio no vuelve a establecer automáticamente la propiedad **ReferenceAssemblyFromVbaProject** en **False**. Puede establecer esta propiedad en **False** manualmente mediante la ventana **Propiedades** .

### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject
 Al establecer la propiedad **ReferenceAssemblyFromVbaProject** de cualquier elemento host de un proyecto de Visual Basic o Visual C# en **True**, Visual Studio realiza las siguientes tareas:

1. Genera una biblioteca de tipos para el ensamblado de personalización e incrusta la biblioteca de tipos en el ensamblado.

2. Agrega una referencia a las siguientes bibliotecas de tipos en el proyecto de VBA del documento:

   - La biblioteca de tipos para el ensamblado de personalización.

   - La biblioteca de tipos de Microsoft Visual Studio Tools para Office Execution Engine 9.0. Esta biblioteca de tipos está incluida en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

   Cuando la propiedad **ReferenceAssemblyFromVbaProject** se vuelve a establecer en **False**, Visual Studio realiza las siguientes tareas:

3. Quita las referencias de la biblioteca de tipos del proyecto de VBA del documento.

4. Quita la biblioteca de tipos incrustada del ensamblado.

## <a name="troubleshoot"></a>Solución de problemas
 En la tabla siguiente se enumeran algunos errores comunes y sugerencias para corregir los errores.

|Error|Sugerencia|
|-----------|----------------|
|Después de establecer la propiedad **EnableVbaCallers** o **ReferenceAssemblyFromVbaProject** , un mensaje de error indica que el documento no contiene un proyecto de VBA o que no tiene permiso de acceso al proyecto de VBA en el documento.|Asegúrese de que el documento del proyecto contenga al menos una macro VBA, de que el proyecto de VBA tenga la confianza suficiente para ejecutarse y de que el proyecto de VBA no esté protegido mediante contraseña.|
|Después de establecer la propiedad **EnableVbaCallers** o **ReferenceAssemblyFromVbaProject** , un mensaje de error indica que falta la declaración <xref:System.Runtime.InteropServices.GuidAttribute> o está dañada.|Asegúrese de que la <xref:System.Runtime.InteropServices.GuidAttribute> declaración se encuentre en el archivo *AssemblyInfo.CS* o *AssemblyInfo. VB* del proyecto y que este atributo esté establecido en un GUID válido.|
|Después de establecer la propiedad **EnableVbaCallers** o **ReferenceAssemblyFromVbaProject** , un mensaje de error indica que el número de versión especificado por el <xref:System.Reflection.AssemblyVersionAttribute> no es válido.|Asegúrese de que la <xref:System.Reflection.AssemblyVersionAttribute> declaración del archivo *AssemblyInfo.CS* o *AssemblyInfo. VB* del proyecto esté establecida en un número de versión de ensamblado válido. Para obtener información sobre los números de versión de ensamblado válidos, vea la clase <xref:System.Reflection.AssemblyVersionAttribute> .|
|Después de cambiar el nombre del ensamblado de personalización, el código VBA que llama al ensamblado de personalización deja de funcionar.|Si cambia el nombre del ensamblado de personalización después exponerlo a código VBA, se rompe el vínculo entre el proyecto de VBA del documento y el ensamblado de personalización. Para corregir este problema, cambie la propiedad **ReferenceFromVbaAssembly** del proyecto a **False** y luego de nuevo a **True**y, a continuación, reemplace cualquier referencia al antiguo nombre del ensamblado del código VBA por el nuevo nombre del ensamblado.|

## <a name="see-also"></a>Consulte también
- [Cómo: exponer código a VBA en un proyecto de Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Cómo: exponer código a VBA en un proyecto de&#35; de Visual C](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Tutorial: llamar a código desde VBA en un proyecto de Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Tutorial: llamar a código desde VBA en un proyecto de&#35; de Visual C](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Comparación de las soluciones de VBA y Office en Visual Studio](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)
- [Personalizaciones de nivel de documento de programa](../vsto/programming-document-level-customizations.md)
