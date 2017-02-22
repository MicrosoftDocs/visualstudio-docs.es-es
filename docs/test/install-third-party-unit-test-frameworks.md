---
title: "Instalar marcos de prueba unitaria de terceros | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "mlearned"
manager: "douge"
---
# Instalar marcos de prueba unitaria de terceros
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Explorador de pruebas de Visual Studio puede ejecutar cualquier marco de pruebas que haya desarrollado una interfaz de adaptador para el explorador.  El programa de instalación del marco instala los binarios y agrega plantillas del proyecto de Visual Studio para los idiomas que admite.  Cuando crea un proyecto con la plantilla, el marco se registra en el Explorador de pruebas.  Una solución de Visual Studio puede contener proyectos de prueba unitaria que usen diferentes marcos y que estén destinados a diferentes idiomas.  El Explorador de pruebas los ejecuta todos.  
  
 **Requisitos**  
  
-   Visual Studio Enterprise, Visual Studio Professional  
  
## Adquirir marcos de terceros  
 Puede descargar e instalar numerosos marcos de pruebas unitarias de terceros mediante el Administrador de extensiones de Visual Studio o desde la Galería de Visual Studio en el sitio web de MSDN.  Los marcos también pueden descargarse desde otros sitios, como el sitio web del marco.  
  
### Instalación desde Visual Studio  
  
1.  En el menú estándar, seleccione **Herramientas** y, a continuación, elija **Extensiones y actualizaciones**.  
  
2.  Expanda **En línea**, **Galería de Visual Studio**, **Herramientas**.  Seleccione **Pruebas**.  
  
3.  Examine la lista para buscar el marco.  
  
4.  Seleccione el marco y elija **Descargar**.  
  
 Para obtener más información, consulte [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
### Instalación desde la Web  
 Si sabe qué marco le interesa, realice lo siguiente:  
  
1.  Abra la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=236267) en el sitio Web MSDN.  
  
2.  Escriba el nombre del marco en el cuadro **Buscar**.  
  
3.  Elija el marco en la lista de resultados para desplazarse a la página de la Galería de Visual Studio de la herramienta.  
  
 Para examinar una lista de los marcos junto con otras herramientas de pruebas, realice lo siguiente:  
  
1.  Abra la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=236267) en el sitio Web MSDN.  
  
2.  Seleccione **Examinar**.  
  
3.  En la lista **Categoría**, amplíe el nodo **Herramientas** y, a continuación, seleccione **Pruebas**.  
  
4.  Elija un marco en la lista de resultados para desplazarse a la página de la Galería de Visual Studio de la herramienta.  
  
## Vea también  
 [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)