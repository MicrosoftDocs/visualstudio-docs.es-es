---
title: "Procedimientos recomendados para usar fragmentos de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fragmentos de código, procedimientos recomendados"
  - "fragmentos de código, seguridad"
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedimientos recomendados para usar fragmentos de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El código de un fragmento de código muestra sólo la manera más básica de hacer algo.  Para la mayoría de las aplicaciones, el código debe modificarse para ajustarse a la aplicación.  
  
## Controlar las excepciones  
 Normalmente, los bloques try\-catch de fragmentos de código… detectan y volver a producir todas las excepciones.  Es posible que no sea la elección más adecuada para su proyecto.  Existen varias formas de responder a cada excepción.  Para obtener ejemplos, vea [Cómo: Controlar una excepción mediante Try y Catch](../Topic/How%20to:%20Handle%20an%20Exception%20Using%20try-catch%20\(C%23%20Programming%20Guide\).md) y [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).  
  
## Ubicaciones de archivos  
 Cuando adapte las ubicaciones del archivo a la aplicación, debe considerar lo siguiente:  
  
-   Encontrar una ubicación accesible.  Los usuarios no pueden obtener acceso a la carpeta Archivos de programa del equipo, de modo que almacenar los archivos con los archivos de aplicación no funcione.  
  
-   Encontrar una ubicación segura.  Los archivos almacenados en la carpeta raíz \(C:\\\) no es seguro.  Para los datos de la aplicación, recomendamos la carpeta \\Datos de programa.  Para los datos de cada usuario, la aplicación puede crear un archivo en la carpeta \\Mis documentos.  
  
-   Utilizar un nombre de archivo válido.  Puede utilizar los controles de <xref:System.Windows.Forms.OpenFileDialog> y de <xref:System.Windows.Forms.SaveFileDialog> para reducir la probabilidad de nombres de archivo no válidos.  Tenga en cuenta que en el período comprendido entre el momento en que el usuario selecciona el archivo y el momento en que el código manipula el archivo, este archivo puede eliminarse.  Además, es posible que el usuario no tenga los permisos para escribir en el archivo.  
  
## Seguridad  
 Lo seguro que sea un miniprograma depende de en qué parte del código fuente se utilice y de cómo se modifique una vez que está en el código.  La lista siguiente contiene algunas de las áreas que deben tenerse en cuenta.  
  
-   Acceso a archivos y bases de datos  
  
-   Seguridad de acceso del código  
  
-   Protección de recursos \(como registros de eventos, Registro\)  
  
-   Almacenamiento de secretos  
  
-   Comprobación de entradas  
  
-   Transferencia de datos a tecnologías de scripting  
  
 Para obtener más información, vea [Proteger aplicaciones](../ide/securing-applications.md).  
  
## fragmentos de código descargado  
 Los fragmentos de código de IntelliSense instalados por Visual Studio no están en ellos mismos un riesgo de seguridad.  Sin embargo, pueden generar riesgos para la seguridad en la aplicación.  Los fragmentos de código descargados de internet se deben tratar como cualquier otro contenido descargado \- con extrema precaución.  
  
-   Los fragmentos de descarga desde sitios de confianza, y usan software antivirus actualizado.  
  
-   Abra todos los archivos descargados de fragmentos de código en el Bloc de notas o el Editor XML de Visual Studio y los revise cuidadosamente antes de instalarlos.  busque los problemas siguientes:  
  
    -   El código del miniprograma podría dañar el sistema si lo ejecuta.  lea el código fuente cuidadosamente antes de ejecutarlo.  
  
    -   El bloque de la dirección URL de la Ayuda del archivo del miniprograma puede contener las direcciones URL que ejecutan un archivo de script malintencionado o muestran un sitio Web ofensivo.  
  
    -   El fragmento de código puede contener referencias que se agregan automáticamente al proyecto y se puede cargar desde cualquier parte del sistema.  Estas referencias se pueden haber descargado en su equipo desde el sitio del que descargó el fragmento de código.  El fragmento de código puede realizar a continuación una llamada a un método de la referencia que ejecuta el código malintencionado.  Para protegerse contra este tipo de ataque, revise los bloques imports y referencias de archivo snippet.  
  
## Vea también  
 [Fragmentos de código de IntelliSense de Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)   
 [Proteger aplicaciones](../ide/securing-applications.md)   
 [Fragmentos de código](../ide/code-snippets.md)