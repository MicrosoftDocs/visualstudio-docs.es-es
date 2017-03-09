---
title: "Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b0f72a4-70ca-4e55-b236-2ea1034fd8a7
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "mlearned"
manager: "douge"
---
# Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El marco de pruebas de UI codificadas y grabaciones de acciones no admite todas las posibles interfaces de usuario.  Tal vez no admita la interfaz de usuario concreta que desea probar.  Por ejemplo, no puede crear directamente una prueba de IU codificada o una grabación de acciones para una hoja de cálculo de [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  Sin embargo, puede crear una extensión para el marco de pruebas de IU codificadas que admita la interfaz de usuario concreta aprovechando la extensibilidad del marco de pruebas de IU codificadas.  En el siguiente tema se proporciona un ejemplo de cómo extender el marco para que admita la creación de pruebas de IU codificadas y grabaciones de acciones para [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  Para obtener más información acerca de las plataformas compatibles, consulte [Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).  
  
 **Requisitos**  
  
-   Visual Studio Enterprise  
  
 En esta sección se presenta una extensión de prueba de IU codificada que puede grabar y reproducir pruebas para hojas de cálculo de Excel.  Cada parte de la extensión se explica en esta sección y en los comentarios de código para los desarrolladores que desean crear este tipo de extensión.  
  
 ![Arquitectura de pruebas de IU](../test/media/ui_testarch.png "UI\_TestArch")  
Información general sobre la arquitectura  
  
## Descargar el ejemplo  
 El ejemplo está compuesto por cuatro proyectos en la solución `CodedUIExtensibilitySample.sln`:  
  
-   CodedUIextensibilitySample  
  
-   ExcelCodedUIAddInHelper  
  
-   ExcelUICommunicationHelper  
  
-   SampleTestProject  
  
 Obtenga el ejemplo de esta [publicación del blog](http://go.microsoft.com/fwlink/?LinkID=185592).  
  
> [!NOTE]
>  El ejemplo está pensado para usarse con Microsoft Excel 2010.  El ejemplo puede funcionar en otras versiones de Microsoft Excel, pero actualmente no se admite.  
  
## Detalles sobre el ejemplo  
 En las siguientes secciones se proporciona información sobre el ejemplo y su estructura.  
  
### Complemento de Microsoft Excel: ExcelCodedUIAddinHelper  
 Este proyecto incluye un complemento que se ejecuta en el proceso de Excel.  Consulte [Complemento de Excel de muestra para probar la IU codificada](../test/sample-excel-add-in-for-coded-ui-testing.md) para obtener una descripción breve del proyecto de complemento.  
  
 Para obtener más información, consulte [Tutorial: Crear el primer complemento de VSTO para Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md).  
  
### Comunicación de Interfaz de usuario de Excel: ExcelUIcommunicationHelper  
 Este proyecto incluye la interfaz de `IExcelUICommunication` y las clases de información que se usan para intercambiar datos entre el marco de trabajo de pruebas de IU codificada y Excel.  Para obtener más información, consulte [Interfaz de muestra del Communicator de Excel](../test/sample-excel-communicator-interface.md).  
  
### Extensión de prueba de UI codificada: CodedUIExentsibilitySample  
 Este proyecto incluye las clases personalizadas que se utilizan en pruebas de una hoja de cálculo de Excel.  El código de cada una de estas clases es bastante autoexplicativo.  Sin embargo, se proporciona una breve descripción de cada clase personalizada.  Para obtener más información, consulte [Extensión de muestra para probar la IU codificada para Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
### Implementar el complemento y la extensión  
 Después de haber creado todos los proyectos y objetos, ejecute el archivo `CopyDrop.bat` como un administrador.  Este archivo copia los archivos DLL y PDB `ExcelCodedUIAddinHelper` en:  
  
 "`%CommonProgramFiles(x86)%\Microsoft Shared\VSTT\<version number>\UITestExtensionPackages\*.*`", donde el número de versión podría ser 11.0, 12.0, etc., según su versión de Visual Studio.  
  
 Los archivos DLL y PDB `ExcelUICommunicationHelper` se copian en `"%ProgramFiles(x86)%\Microsoft Visual Studio <version number>\Common7\IDE\PrivateAssemblies”`.  
  
 Tal vez tenga que ajustar las rutas de acceso de la copia, pero no se requiere ninguna instalación adicional.  En una máquina de 64 bits, use el símbolo del sistema de Visual Studio Enterprise de 32 bits para ejecutar el archivo `CopyDrop.bat`.  
  
### Probar Excel con SampleTestProject  
 Puede hacer la prueba en el proyecto de prueba que usa una versión concreta de Excel que a lo mejor no tiene o crear un proyecto de prueba y grabar una prueba propia.  Para obtener más información, vea [Crear pruebas de IU codificadas](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Usar la automatización de IU para probar el código](../test/use-ui-automation-to-test-your-code.md)   
 [Procedimientos recomendados para las pruebas de IU codificadas](../test/best-practices-for-coded-ui-tests.md)   
 [Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)