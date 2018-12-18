---
title: Llamar a código en complementos VSTO desde otras soluciones de Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9290fcdd705f6f38b4b7e91e46d5b635f1e309ff
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248103"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Llamar a código en complementos VSTO desde otras soluciones de Office
  Puede exponer un objeto en su complemento VSTO para otras soluciones, incluidas otras soluciones de Microsoft Office. Esto resulta útil si su complemento VSTO proporciona un servicio que quiera habilitar para que lo usen otras soluciones. Por ejemplo, si tiene un complemento VSTO para Microsoft Office Excel que realiza cálculos sobre datos financieros desde un servicio Web, otras soluciones pueden realizar estos cálculos llamando al complemento VSTO de Excel en tiempo de ejecución.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Hay dos pasos principales en este proceso:  
  
-   En el complemento VSTO, exponga un objeto a otras soluciones.  
  
-   En otra solución, acceda al objeto expuesto por el complemento VSTP y llame a los miembros del objeto.  
  
## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Tipos de soluciones que pueden llamar a código en un complemento  
 Puede exponer un objeto en un complemento de VSTO a los siguientes tipos de soluciones:  
  
-   Código de Visual Basic para Aplicaciones (VBA) en un documento que se carga en el mismo proceso de aplicación que el complemento VSTO.  
  
-   Personalizaciones de nivel de documento que se cargan en el mismo proceso de aplicación que el complemento VSTO.  
  
-   Otros complementos VSTO creados con plantillas de proyecto de Office en Visual Studio.  
  
-   Complementos COM VSTO (es decir, complementos que implementan la interfaz <xref:Extensibility.IDTExtensibility2> directamente).  
  
-   Cualquier solución que se ejecute en un proceso diferente que el complemento VSTO (estos tipos de soluciones también se llaman *clientes fuera de proceso*). Estas soluciones incluyen aplicaciones que automatizan una aplicación de Office, como Windows Forms o la aplicación de consola, y complementos VSTO que se cargan en un proceso diferente.  
  
## <a name="expose-objects-to-other-solutions"></a>Exponer objetos a otras soluciones  
 Para exponer un objeto del complemento VSTO en otras soluciones, siga estos pasos en el complemento VSTO:  
  
1.  Defina una clase que quiera exponer a otras soluciones.  
  
2.  Invalide el método <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> en la clase `ThisAddIn` . Devuelva una instancia de la clase que quiere exponer a otras soluciones.  
  
### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Definir la clase que desea exponer a otras soluciones  
 Como mínimo, la clase que quiera exponer tiene que ser pública, debe tener el atributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en **true**y debe exponer la interfaz [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) .  
  
 La manera recomendada de exponer la interfaz [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) es realizar los siguientes pasos:  
  
1. Defina una interfaz que declare los miembros que quiere exponer a otras soluciones. Puede definir esta interfaz en su proyecto de complemento VSTO. Sin embargo, puede que quiera definir esta interfaz en un proyecto de biblioteca de clase diferente, si quiere exponer la clase a soluciones que no son VBA; de ese modo, las soluciones que llaman al complemento VSTO pueden hacer referencia a la interfaz sin hacer referencia al proyecto de complemento VSTO.  
  
2. Aplique el atributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> a esta interfaz y establezca el atributo en **true**.  
  
3. Modifique la clase para implementar esta interfaz.  
  
4. Aplicar el <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> a la clase de atributo y establezca este atributo en el **ninguno** valor de la <xref:System.Runtime.InteropServices.ClassInterfaceType> enumeración.  
  
5. Si desea exponer esta clase a clientes fuera de proceso, también es posible que deba hacer lo siguiente:  
  
   -   Derive la clase de <xref:System.Runtime.InteropServices.StandardOleMarshalObject>. Para obtener más información, consulte [exponer clases a clientes fuera de proceso](#outofproc).  
  
   -   Establezca la propiedad **Registrar para interoperabilidad COM** en el proyecto donde define la interfaz. Esta propiedad solo es necesaria si desea permitir que los clientes usen enlace temprano para llamar al complemento VSTO.  
  
   El siguiente ejemplo de código muestra una clase `AddInUtilities` con un método `ImportData` al que otras soluciones pueden llamar. Para ver este código en el contexto de un tutorial más amplio, consulte [Tutorial: Llamar a código en un complemento de VSTO desde VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
   [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
   [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
### <a name="expose-classes-to-vba"></a>Exponer clases a VBA  
 Cuando realice los pasos indicados arriba, el código VBA podrá llamar solo a los métodos que declare en la interfaz. El código VBA no puede llamar a ningún otro método de la clase, incluidos los métodos que la clase obtiene a partir de clases base, como <xref:System.Object>.  
  
 Alternativamente, puede exponer el [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interfaz estableciendo el <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> en el valor en AutoDispatch o AutoDual del <xref:System.Runtime.InteropServices.ClassInterfaceType> enumeración. Si expone la interfaz, no es necesario declarar los métodos en una interfaz independiente. Sin embargo, el código VBA puede llamar a cualquier método público y no estático de su clase, incluidos los métodos obtenidos a partir de clases base tales como <xref:System.Object>. Además, los clientes fuera de proceso que usan enlace temprano no pueden llamar a su clase.  
  
###  <a name="outofproc"></a> Exponer clases a clientes fuera de proceso  
 Si quiere exponer una clase de su complemento de VSTO a clientes fuera de proceso, debe derivar la clase de <xref:System.Runtime.InteropServices.StandardOleMarshalObject> para asegurarse de que los clientes fuera de proceso puedan llamar al objeto de complemento de VSTO expuesto. De lo contrario, se podrían producir errores inesperados al intentar obtener una instancia del objeto expuesto en un cliente fuera de proceso.  
  
 Este error es porque todas las llamadas al modelo de objetos de una aplicación de Office deben realizarse en el subproceso de interfaz de usuario principal, pero las llamadas desde un cliente fuera de proceso al objeto llegarán en subproceso RPC (llamada a procedimiento remoto) arbitrario. El mecanismo de cálculo de referencias COM en .NET Framework no cambiará los subprocesos y, en cambio, intentará calcular las referencias de la llamada al objeto en el subproceso de RPC entrante en lugar del subproceso principal de interfaz de usuario. Si el objeto es una instancia de una clase que deriva de <xref:System.Runtime.InteropServices.StandardOleMarshalObject>, el cálculo de las referencias de las llamadas entrantes al objeto se realizará en el subproceso donde se creó el objeto expuesto, que será el subproceso principal de interfaz de usuario de la aplicación host.  
  
 Para obtener más información sobre cómo usar subprocesos en soluciones de Office, consulte [compatibilidad del subprocesamiento en Office](../vsto/threading-support-in-office.md).  
  
### <a name="override-the-requestcomaddinautomationservice-method"></a>Invalide el método RequestComAddInAutomationService  
 El ejemplo de código siguiente muestra cómo invalidar <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> en la clase `ThisAddIn` del complemento de VSTO. El ejemplo se supone que ha definido una clase denominada `AddInUtilities` que desea exponer a otras soluciones. Para ver este código en el contexto de un tutorial más amplio, consulte [Tutorial: Llamar a código en un complemento de VSTO desde VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
 Una vez cargado el complemento de VSTO, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] llama al método <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . El tiempo de ejecución asigna el objeto devuelto a la propiedad COMAddIn.Object de un <xref:Microsoft.Office.Core.COMAddIn> objeto que representa el complemento VSTO. Este objeto <xref:Microsoft.Office.Core.COMAddIn> está disponible para otras soluciones de Office y para soluciones que automatizan Office.  
  
## <a name="access-objects-from-other-solutions"></a>Obtener acceso a objetos desde otras soluciones  
 Para llamar al objeto expuesto en el complemento de VSTO, siga estos pasos en la solución cliente:  
  
1. Obtenga el objeto <xref:Microsoft.Office.Core.COMAddIn> que representa el complemento de VSTO expuesto. Los clientes pueden acceder a todos los complementos de VSTO disponibles usando la propiedad `Application.COMAddIns` del modelo de objetos de la aplicación host de Office.  
  
2. Acceso a la propiedad COMAddIn.Object de la <xref:Microsoft.Office.Core.COMAddIn> objeto. Esta propiedad devuelve el objeto expuesto desde el complemento de VSTO.  
  
3. Llame a los miembros del objeto expuesto.  
  
   La forma que utiliza el valor devuelto de la propiedad COMAddIn.Object es diferente para los clientes de VBA y que no son VBA. En los clientes fuera de proceso, es necesario código adicional para evitar una posible condición de carrera.  
  
### <a name="access-objects-from-vba-solutions"></a>Obtener acceso a objetos desde soluciones VBA  
 En el ejemplo de código siguiente se muestra cómo usar VBA para llamar a un método que se expone mediante un complemento de VSTO. Esta macro VBA llama a un método denominado `ImportData` que se define en un complemento de VSTO que se denomina **ExcelImportData**. Para ver este código en el contexto de un tutorial más amplio, consulte [Tutorial: Llamar a código en un complemento de VSTO desde VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
```vb
Sub CallVSTOMethod()  
    Dim addIn As COMAddIn  
    Dim automationObject As Object  
    Set addIn = Application.COMAddIns("ExcelImportData")  
    Set automationObject = addIn.Object  
    automationObject.ImportData  
End Sub  
```  
  
### <a name="access-objects-from-non-vba-solutions"></a>Obtener acceso a objetos desde soluciones que no son VBA  
 En una solución que no son VBA, debe convertir el valor de propiedad COMAddIn.Object a la interfaz que implementa y, a continuación, puede llamar a los métodos expuestos en el objeto de interfaz. El ejemplo de código siguiente muestra cómo llamar al método `ImportData` desde un complemento de VSTO diferente que se creó usando las herramientas de desarrollador de Office en Visual Studio.  
  
```vb  
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")  
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _  
    addIn.Object, ExcelImportData.IAddInUtilities)  
utilities.ImportData()  
```  
  
```csharp  
object addInName = "ExcelImportData";  
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);  
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;  
utilities.ImportData();  
```  
  
 En este ejemplo, si se intenta convertir el valor de la propiedad COMAddIn.Object a la `AddInUtilities` clase en lugar de `IAddInUtilities` interfaz, el código iniciará una <xref:System.InvalidCastException>.  
  
## <a name="see-also"></a>Vea también  
 [Programar complementos VSTO](../vsto/programming-vsto-add-ins.md)   
 [Tutorial: Llamar a código en un complemento de VSTO desde VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Personalizar las características de interfaz de usuario mediante interfaces de extensibilidad](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  
