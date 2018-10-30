---
title: Crear un proyecto de prueba unitaria | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a608bfba-1a43-4a60-b73a-1fe53ef58098
caps.latest.revision: 10
ms.author: gewarren
manager: douge
ms.openlocfilehash: 92520f2b092d3ef8b3daa3f4ffa41139a18d6641
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883424"
---
# <a name="create-a-unit-test-project"></a>Crear un proyecto de prueba unitaria
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las pruebas unitarias a menudo reflejan la estructura del código sometido a pruebas. Por ejemplo, se crearía un proyecto de prueba unitaria para cada proyecto de código en el producto. El proyecto de prueba puede estar en la misma solución que el código de producción, o puede estar en una solución independiente. Puede tener varios proyectos de prueba unitaria en una solución.  
  
> [!NOTE]
>  La ubicación de las pruebas unitarias para código nativo y la estructura del proyecto de prueba puede ser diferente de la estructura que se describe en este tema. Para obtener más información, consulte [Agregar pruebas unitarias a aplicaciones C++ existentes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md).  
  
## <a name="to-create-a-unit-test-project"></a>Para crear un proyecto de prueba unitaria:  
  
1.  En el menú **Archivo** , elija **Nuevo** y, a continuación, **Proyecto** (Ctrl + Mayús + N en el teclado).  
  
2.  En el cuadro de diálogo Nuevo proyecto, expanda el nodo **Instalado**, elija el lenguaje que desea usar para el proyecto de prueba y después **Probar**.  
  
3.  Para usar uno de los marcos de pruebas unitarias de Microsoft, elija **Proyecto de prueba unitaria** en la lista de plantillas de proyecto. De lo contrario, elija la plantilla de proyecto del marco de pruebas unitarias que desea usar. Para probar el proyecto Cuentas del ejemplo, el proyecto se denominaría CuentasPrueba.  
  
4.  En el proyecto de prueba unitaria, agregue una referencia al código en pruebas.  Aquí se muestra cómo crear la referencia a un proyecto de código en la misma solución:  
  
    1.  Seleccione el proyecto en el Explorador de soluciones.  
  
    2.  En el menú **Proyecto**, elija **Agregar referencia**.  
  
    3.  En el cuadro de diálogo Administrador de referencias, abra el nodo **Solución** y elija **Proyectos**. Compruebe el nombre del proyecto de código y cierre el cuadro de diálogo.  
  
5.  Si el código que desea probar está en otra ubicación, consulte [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md) para obtener información sobre cómo agregar referencias.  
  
## <a name="next-steps"></a>Pasos siguientes  
 **Escribir pruebas unitarias**  
  
 Consulte una de las siguientes secciones:  
  
- [Escribir pruebas unitarias para .NET Framework con el Framework de pruebas unitarias de Microsoft para código administrado](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)  
  
- [Escribir pruebas unitarias para C/C++ con el Framework de pruebas unitarias de Microsoft para C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)  
  
  **Ejecutar pruebas unitarias**  
  
  [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)



