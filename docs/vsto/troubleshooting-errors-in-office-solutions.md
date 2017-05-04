---
title: "Solucionar problemas de errores de las soluciones de Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Project.DesignerDisabled"
  - "VST.Designer.CannotActivate"
  - "VST.Project.ExcelBusy"
  - "VST.SelectDocWizard.AlreadyCustomized"
  - "VST.SelectDocWizard.DocPath"
  - "VST.Project.CannotOpen"
  - "VST.Designer.ErrorsOccurred"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "solución de problemas [desarrollo de Office en Visual Studio]"
ms.assetid: 8bbf5433-1992-4ecf-ae1b-19117b8ebe43
caps.latest.revision: 69
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 68
---
# Solucionar problemas de errores de las soluciones de Office
  Pueden surgir problemas al realizar las siguientes tareas mientras desarrolla soluciones de Office en Visual Studio:  
  
-   [Crear, actualizar y abrir proyectos](#creating)  
  
-   [Usar los diseñadores](#designers)  
  
-   [Escribir código](#code)  
  
-   [Compilar proyectos](#building)  
  
-   [Depurar proyectos](#debugging)  
  
##  <a name="creating"></a> Crear, actualizar y abrir proyectos  
 Pueden producirse los siguientes errores al crear o abrir proyectos de Office.  
  
### No se puede crear el proyecto  
 Se produjo un error cuando intentaba crear o abrir un proyecto de Office, pero Visual Studio no disponía de información suficiente para determinar la causa.  Intente cerrar el proyecto, salga de Visual Studio y comience de nuevo.  
  
 Si está intentando crear un proyecto de nivel de documento, es posible que otro documento con el mismo nombre que el documento del proyecto nuevo ya esté abierto en Excel o Word.  Asegúrese de que están cerradas todas las demás instancias de Excel o Word.  
  
### Las propiedades del control se pierden cuando se crea un proyecto nuevo basado en un documento de un proyecto existente  
 Si crea un nuevo proyecto de Office basado en un documento de un proyecto existente, las propiedades de los controles que están en el documento no se copian en el proyecto nuevo.  Debe restablecer manualmente las propiedades de todos los controles preexistentes.  Como alternativa, puede conservar las propiedades del control creando una copia del proyecto existente en lugar de crear un proyecto nuevo, o cargando el proyecto existente en una solución nueva \(en el diseñador\) para copiar y pegar los controles del documento existente en el documento nuevo.  
  
### Errores al crear un proyecto de libro de Excel basado en un libro existente  
 Si crea un nuevo proyecto de libro de Excel basado en un libro existente, podría ver una combinación de los siguientes errores.  
  
 En Excel: "Advertencia de privacidad: este documento contiene macros, controles ActiveX, información del paquete de expansión XML o componentes web.  Pueden incluir información personal que el Inspector de documento no puede quitar".  
  
 En Visual Studio: "El diseñador no se pudo cargar correctamente".  
  
 Estos errores pueden producirse al intentar crear un proyecto basado en un libro cuya información personal se quitó mediante el Inspector de documento.  Para evitar este error, lleve a cabo los pasos siguientes antes de crear el proyecto.  
  
1.  Abra el libro en Excel.  
  
2.  En Excel, abra el Centro de confianza.  
  
3.  En la pestaña **Opciones de privacidad**, desactive la casilla **Quitar información personal de las propiedades del archivo al guardar**.  
  
4.  Guarde el libro y cierre Excel.  
  
### No se puede abrir un proyecto después de la migración  
 Después de migrar una solución de Office a Microsoft Office 2010, el proyecto no se puede abrir en un equipo de desarrollo que solo tiene instalado 2007 Microsoft Office System.  Es posible que vea los siguientes errores.  
  
 "Uno o varios proyectos de la solución no se cargaron correctamente.  Consulte la ventana de salida para obtener más información".  
  
 "No se puede crear el proyecto porque la aplicación asociada a este tipo de proyecto no está instalada en este equipo.  Debe instalar la aplicación de Microsoft Office que está asociada a este tipo de proyecto".  
  
 Para resolver este problema, edite el archivo .vbproj o .csproj.  En el caso de un proyecto de Word, reemplace HostPackage\="{763FDC83\-64E5\-4651\-AC9B\-28C4FEB985A1}" por HostPackage\="{6CE98B71\-D55A\-4305\-87A8\-0D6E368D9600}".  En el caso de un proyecto de Excel, reemplace HostPackage\="{B284B16A\-C42C\-4438\-BDCD\-B72F4AC43CFB}" por HostPackage\="{825100CF\-0BA7\-47EA\-A084\-DCF3308DAF74}".  En el caso de un proyecto de Outlook, reemplace HostPackage\="{D2B20FF5\-A6E5\-47E1\-90E8\-463C6860CB05}" por HostPackage\="{20A848B8\-E01F\-4801\-962E\-25DB0FF57389}".  
  
 Como alternativa, asegúrese de que los proyectos migrados solo se abren en equipos de desarrollo con Microsoft Office 2010 instalado.  
  
### Errores en los proyectos de nivel de documento de Office 2003 actualizados que contienen controles de Windows Forms  
 Si actualiza un proyecto de nivel de documento de Microsoft Office 2003 y el documento contiene controles de Windows Forms, el proyecto actualizado podría tener errores en tiempo de compilación o ejecución.  Para evitar este problema, instale Runtime de Visual Studio 2005 Tools para Office Second Edition en el equipo de desarrollo antes de actualizar el proyecto.  Esta versión del runtime está disponible como paquete redistribuible en el Centro de descarga de Microsoft en [Microsoft Visual Studio 2005 Tools para Office Second Edition Runtime \(VSTO 2005 SE\) \(x86\)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
 Cuando termine de actualizar el proyecto, puede desinstalar Visual Studio 2005 Tools para Office Second Edition Runtime en el equipo de desarrollo si no lo usa ninguna otra solución de Office.  
  
##  <a name="designers"></a> Usar los diseñadores  
 Podría encontrar los siguientes errores al trabajar con el documento, el libro o el diseñador de hojas de cálculo en proyectos de nivel de documento.  
  
### El diseñador no se pudo cargar correctamente  
 Visual Studio no puede abrir el diseñador en los casos siguientes:  
  
-   Excel o Word ya están abiertos y muestran un cuadro de diálogo modal.  Para abrir el diseñador, compruebe si Excel o Word tienen abierto un cuadro de diálogo modal y cierre todos los cuadros de diálogo modales que estén abiertos.  Si no hay ningún cuadro de diálogo modal abierto, podría ser necesaria otra acción para que Excel o Word respondan.  
  
-   El proyecto se está depurando.  Para abrir el diseñador, detenga o finalice la depuración.  
  
-   Un complemento de VSTO de Excel que está instalado en el equipo de desarrollo muestra un cuadro de diálogo cuando se inicia Excel.  Para crear un proyecto de nivel de documento de Excel, primero debe deshabilitar el complemento de VSTO.  
  
### Los controles aparecen como rectángulos negros en el documento o la hoja de cálculo  
 Si agrupa los controles en un documento o una hoja de cálculo, Visual Studio ya no los reconoce.  No se puede acceder a los controles agrupados en la ventana **Propiedades** y aparecen como rectángulos negros en el documento o la hoja de cálculo.  Debe desagrupar los controles para restaurar su funcionalidad.  
  
### Los controles de una plantilla de Word no están visibles en Visual Studio  
 Si abre una plantilla de Word en el diseñador de Visual Studio, los controles de la plantilla que no están en línea con el texto no estarán visibles.  Esto se debe a que Visual Studio abre las plantillas de Word en la vista **Normal**.  Para ver los controles, haga clic en el menú **Vista**, seleccione **Vista de Microsoft Office Word** y haga clic en **Diseño de impresión**.  
  
### El comando Insertar imagen prediseñada no hace nada en el diseñador de Visual Studio  
 Cuando Excel o Word están abiertos en el diseñador de Visual Studio, si se hace clic en el botón **Imágenes prediseñadas** situado en la pestaña **Ilustraciones** en la cinta de opciones no se abre el panel de tareas **Imágenes prediseñadas**.  Para agregar imágenes prediseñadas, debe abrir la copia del libro o del documento que se encuentra en la carpeta de proyecto principal \(no la copia que está en la carpeta \\bin\) fuera de Visual Studio, agregar las imágenes prediseñadas y, a continuación, guardar el libro o el documento.  
  
##  <a name="code"></a> Escribir código  
 Pueden producirse los siguientes errores al escribir código en proyectos de Office.  
  
### Algunos eventos de objetos de Office no están accesibles al usar C\#  
 En algunos casos, podría ver un error del compilador similar al siguiente al intentar acceder a un evento determinado de una instancia de un tipo de ensamblado de interoperabilidad primario \(PIA\) de Office en un proyecto de Visual C\#.  
  
 "Ambigüedad entre 'Microsoft.Office.Interop.Excel.\_Application.NewWorkbook' y 'Microsoft.Office.Interop.Excel.AppEvents\_Event.NewWorkbook'"  
  
 Este error significa que está intentando acceder a un evento que tiene el mismo nombre que otra propiedad o método del objeto.  Para acceder al evento, debe convertir el objeto a su *interfaz eventos*.  
  
 Los tipos de PIA de Office que tienen eventos implementan dos interfaces: una interfaz básica con todas las propiedades y métodos, y una interfaz de eventos que contiene los eventos expuestos por el objeto.  Estas interfaces de eventos usan la convención de nomenclatura *objectname*Events*n*\_Event, como <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> y <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event>.  Si no puede acceder a un evento que espera encontrar en un objeto, convierta el objeto a su interfaz de eventos.  
  
 Por ejemplo, los objetos <xref:Microsoft.Office.Interop.Excel.Application> tienen un evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> y una propiedad <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A>.  Para controlar el evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook>, convierta <xref:Microsoft.Office.Interop.Excel.Application> a la interfaz <xref:Microsoft.Office.Interop.Excel.AppEvents_Event>.  En el ejemplo de código siguiente se muestra cómo hacerlo desde un proyecto de nivel de documento para Excel.  
  
 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingExcel/CS/ThisWorkbook.cs#1)]  
  
 Para obtener más información sobre las interfaces de eventos en los PIA de Office, consulte [Información general sobre las clases y las interfaces de los ensamblados de interoperabilidad primarios de Office](http://msdn.microsoft.com/es-es/da92dc3c-8209-44de-8095-a843659368d5).  
  
### No se puede hacer referencia a clases de los PIA de Office en proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 En los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], no se compilará de forma predeterminada el código que hace referencia a una clase que se define en un PIA de Office.  Las clases de los PIA usan la convención de nomenclatura *objectname*Class, como <xref:Microsoft.Office.Interop.Word.DocumentClass> y <xref:Microsoft.Office.Interop.Excel.WorkbookClass>.  Por ejemplo, no se compilará el código siguiente desde un proyecto de complemento de VSTO de Word.  
  
```vb  
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 Este código produce los siguientes errores de compilación:  
  
-   En Visual Basic: "No se permite una referencia a la clase ‘DocumentClass’ cuando su ensamblado está vinculado mediante el modo No\-PIA".  
  
-   En Visual C\#: "El tipo de interoperabilidad ‘Microsoft.Office.Interop.Word.DocumentClass’ no se puede incrustar.   Use la interfaz aplicable".  
  
 Para resolver este error, modifique el código para hacer referencia a la interfaz correspondiente.  Por ejemplo, en lugar de hacer referencia a un objeto <xref:Microsoft.Office.Interop.Word.DocumentClass>, haga referencia a una instancia de la interfaz <xref:Microsoft.Office.Interop.Word.Document>.  
  
```vb  
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 Los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] insertan automáticamente todos los tipos de interoperabilidad de los PIA de Office de forma predeterminada.  Este error de compilación se produce porque la característica de tipos de interoperabilidad insertados solo funciona con interfaces, no clases.  Para obtener más información sobre las interfaces y las clases de los PIA de Office, consulte [Información general sobre las clases y las interfaces de los ensamblados de interoperabilidad primarios de Office](http://go.microsoft.com/fwlink/?LinkId=189592).  Para obtener más información sobre la característica de tipos de interoperabilidad insertados en proyectos de Office, consulte [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md).  
  
### No se reconocen las referencias a las clases de Office  
 Algunos nombres de clase, por ejemplo Application, están en varios espacios de nombres, como <xref:Microsoft.Office.Interop.Word> y <xref:System.Windows.Forms>.  Por este motivo, la instrucción **Imports**\/**using** de la parte superior de las plantillas de proyecto incluye una constante calificadora abreviada, por ejemplo:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/CS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/VB/ThisDocument.vb#2)]  
  
 Este uso de la instrucción **Imports**\/**using** requiere distinguir las referencias a las clases de Office con el calificador Word o Excel, por ejemplo:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/CS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/VB/ThisDocument.vb#3)]  
  
 Obtendrá errores si usa una declaración no calificada, por ejemplo:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/CS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/VB/ThisDocument.vb#4)]  
  
 Aunque haya importado el espacio de nombres de Word o Excel y tenga acceso a todas las clases dentro de él, debe calificar totalmente todos los tipos con Word o Excel para eliminar la ambigüedad del espacio de nombres.  
  
##  <a name="building"></a> Compilar proyectos  
 Pueden producirse los siguientes errores al compilar proyectos de Office.  
  
### No se puede compilar un proyecto de nivel de documento basado en un documento con permisos restringidos  
 Visual Studio no puede compilar proyectos de nivel de documento si el documento tiene permisos restringidos.  Si el proyecto contiene un documento con permisos restringidos, no se compilará y recibirá el mensaje siguiente en la ventana **Lista de errores**.  
  
 "No se pudo agregar la personalización".  
  
 Si desea incluir un documento con permisos restringidos, use un documento sin restricciones mientras desarrolla y compila la solución.  A continuación, aplique los permisos restringidos al documento en la ubicación de publicación después de publicar la solución.  
  
### Se producen errores del compilador después de eliminar un control NamedRange  
 Si elimina un control <xref:Microsoft.Office.Tools.Excel.NamedRange> de una hoja de cálculo que no es la hoja de cálculo activa en el diseñador, el código generado automáticamente podría no quitarse del proyecto y podrían producirse errores del compilador.  Para asegurarse de que se quita el código, siempre debe seleccionar la hoja de cálculo que contiene el control <xref:Microsoft.Office.Tools.Excel.NamedRange> para convertirla en la hoja de cálculo activa antes de eliminar el control.  Si el código generado automáticamente no se elimina cuando se elimina el control, puede hacer que el diseñador elimine el código activando la hoja de cálculo y realizando un cambio de modo que la hoja quede marcada como modificada.  Cuando vuelva a compilar el proyecto, el código se quita.  
  
##  <a name="debugging"></a> Depurar proyectos  
 Pueden producirse los siguientes errores al depurar proyectos de Office.  
  
### Se pide confirmación para desinstalar al publicar e instalar una solución en el equipo de desarrollo  
 Cuando se depura una solución de Office, podría ver el siguiente error.  
  
 "No se puede instalar la personalización porque actualmente está instalada otra versión y no se puede actualizar desde esta ubicación".  
  
 Este error indica que previamente publicó e instaló la solución de Office en el equipo de desarrollo.  Para impedir que aparezca el mensaje, desinstale la solución desde la lista de programas instalados en el equipo antes de depurar la solución.  También puede crear otra cuenta de usuario en el equipo de desarrollo para probar la instalación de la solución publicada.  
  
### Los proyectos de nivel de documento creados en ubicaciones de red UNC no se ejecutan desde Visual Studio  
 Si crea un proyecto de nivel de documento para Excel o Word en una ubicación de red UNC, debe agregar la ubicación del documento a la lista de ubicaciones de confianza en Excel o Word.  De lo contrario, la personalización no se cargará cuando intente ejecutar o depurar el proyecto en Visual Studio.  Para obtener más información sobre las ubicaciones de confianza, consulte [Otorgar confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
### Los subprocesos no se detienen correctamente después de la depuración  
 Los proyectos de Office en Visual Studio siguen una convención de nomenclatura de subprocesos que permite al depurador cerrar el programa correctamente.  Si crea subprocesos en la solución, debe asignar al nombre de cada subproceso el prefijo VSTA\_ para asegurarse de que estos subprocesos se controlan correctamente cuando se detiene la depuración.  Por ejemplo, puede establecer la propiedad `Name` de un subproceso que espera un evento de red en VSTA\_NetworkListener.  
  
### No se puede ejecutar o depurar ninguna solución de Office en el equipo de desarrollo  
 Si no puede ejecutar o desarrollar un proyecto de Office en el equipo de desarrollo, podría ver el siguiente mensaje de error.  
  
 "No se pudo cargar la personalización porque no se pudo crear el dominio de la aplicación".  
  
 Visual Studio usa Fusion, el cargador de ensamblados de .NET Framework, para almacenar en caché los ensamblados antes de cargar las soluciones de Office.  Asegúrese de que Visual Studio puede escribir en la caché de Fusion e inténtelo de nuevo.  Para obtener más información, consulte [Copias sombra de ensamblados](../Topic/Shadow%20Copying%20Assemblies.md).  
  
### Error al detener el depurador en un proyecto de nivel de documento después de usar Editar y Continuar  
 Si usa Editar y Continuar para realizar cambios en el código de un proyecto de nivel de documento para Excel o Word mientras el proyecto está en modo de interrupción, podría ver un cuadro de diálogo con el siguiente mensaje de error si el depurador se detiene posteriormente.  
  
 "La terminación del proceso en su estado actual puede provocar resultados inesperados, incluida la pérdida de datos y la inestabilidad del sistema".  
  
 Independientemente de si hace clic en **Sí** o **No** en el cuadro de diálogo, Visual Studio finalizará el proceso de Excel o Word y el depurador se detendrá.  Para detener la depuración del proyecto sin mostrar este cuadro de diálogo, salga de Excel o Word directamente en lugar de detener el depurador en Visual Studio.  
  
## Vea también  
 [Solución de problemas de soluciones de Office](../vsto/troubleshooting-office-solutions.md)   
 [Solucionar problemas de seguridad de soluciones de Office](../vsto/troubleshooting-office-solution-security.md)   
 [Solucionar problemas de implementación de las soluciones de Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  