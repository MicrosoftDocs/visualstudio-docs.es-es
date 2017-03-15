---
title: "C&#243;mo: Administrar archivos de datos locales en los proyectos | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.LocalConnectionConverter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - ".mdb (archivos)"
  - ".mdf (archivos)"
  - "datos [Visual Studio], locales"
  - "datos locales"
  - "mdb (archivos)"
  - "mdf (archivos)"
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
caps.handback.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Administrar archivos de datos locales en los proyectos
Un archivo de base de datos local puede incluirse como un archivo en un proyecto.  La primera vez que conecte la aplicación a un archivo local de base de datos, puede elegir entre crear una copia de la base de datos en el proyecto o conectarse al archivo existente de base de datos en su ubicación actual.  Si elige conectarse al archivo existente, se creará una conexión como si se estuviera conectando a cualquier base de datos remota y se dejará el archivo de base de datos en su ubicación original.  Si elige copiar la base de datos en el proyecto, Visual Studio creará una copia del archivo de base de datos, la agregará al proyecto y modificará la conexión para que señale a la base de datos del proyecto frente a la ubicación original del archivo de base de datos.  
  
> [!NOTE]
>  Las conexiones de datos existentes en el **Explorador de servidores\/Explorador de bases de datos** se modifican para que apunten también al archivo de base de datos del proyecto \(el archivo de base de datos de la carpeta raíz del proyecto\).  
  
 Al compilar un proyecto, el archivo de base de datos podría copiarse de la carpeta de proyecto de raíz en la carpeta de salida \(**bin**\). \(Seleccione **Mostrar todos los archivos** en el **Explorador de soluciones** para ver la carpeta **bin**.\) Este comportamiento se basa en la configuración de la propiedad **Copiar en el directorio de resultados** del archivo.  La configuración predeterminada de la propiedad depende del tipo de archivo de base de datos que utilice.  
  
> [!NOTE]
>  El comportamiento de la propiedad **Copiar en el directorio de resultados** no se aplica a proyectos web o C\+\+.  
  
 Durante el desarrollo de la aplicación, los cambios realizados en los datos \(en tiempo de ejecución dentro de la aplicación\) se harán en la base de datos de la carpeta **bin**.  Por ejemplo, si presiona F5 para depurar la aplicación, se conectará a la base de datos de la carpeta **bin**.  El archivo de base de datos de la carpeta raíz del proyecto se modifica únicamente cuando se edita el esquema o los datos de la base de datos mediante el **Explorador de servidores**\/**Explorador de bases de datos** u otra herramienta de [Visual Database Tools](http://msdn.microsoft.com/es-es/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 La tabla siguiente describe los valores de la propiedad **Copiar en el directorio de salida**.  
  
|Configuración|Comportamiento|  
|-------------------|--------------------|  
|**Copiar si es posterior** \(valor predeterminado para los archivos .sdf\)|El archivo de base de datos se copia del directorio de proyecto en el directorio **bin** la primera vez que se compila el proyecto.  Cada vez subsiguiente que se compila el proyecto, se compara la propiedad **Fecha de modificación** de los archivos.  Si el archivo de la carpeta de proyecto es más reciente, se copia en la carpeta **bin** reemplazando el archivo que contenga.  Si el archivo de la carpeta **bin** es más reciente, no se copia ningún archivo.  Esta configuración guarda los cambios realizados en los datos en tiempo de ejecución, lo que significa que cada vez que ejecute la aplicación y guarde los cambios, esos cambios serán visibles la próxima vez que ejecute la aplicación. **Caution:**  No se recomienda esta opción para los archivos .mdb o .mdf.  El archivo de base de datos puede cambiar aunque no se haya efectuado ningún cambio en los datos.  Simplemente abrir una conexión en un archivo de datos \(por ejemplo, expandiendo el nodo **Tablas** en el **Explorador de servidores**\) puede marcarlo como más reciente.|  
|**Copiar siempre** \(valor predeterminado para los archivos .mdf y .mdb\)|El archivo de base de datos se copia del directorio de proyecto en el directorio \/bin cada vez que se compila la aplicación.  En consecuencia, si compila la aplicación y guarda los cambios del archivo en el directorio \/bin, los cambios se sobrescriben la próxima vez que se copia el archivo original en el directorio \/bin.|  
|**No copiar**|El sistema de proyectos nunca copia ni sobrescribe el archivo.  Debe copiar manualmente el archivo del directorio de proyecto en el directorio de resultados si usa este valor.|  
  
## Procedimiento  
  
#### Para responder al cuadro de diálogo Archivo de base de datos local  
  
-   Haga clic en **Sí** si desea que Visual Studio copie el archivo de base de datos en el proyecto y modifique la conexión para que apunte a la copia del proyecto.  Para obtener más información sobre cómo trabajar con archivos de base de datos en el proyecto, vea [Información general de datos locales](../data-tools/local-data-overview.md).  
  
-   Haga clic en **No** si no desea que Visual Studio copie el archivo de base de datos en el proyecto.  En su lugar, la conexión señala al archivo en la ubicación original y el archivo de base de datos no se agrega como un archivo al proyecto.  
  
## Vea también  
 [Tutorial: Conectar con los datos de un archivo de base de datos local \(Windows Forms\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Tutorial: Conectar a los datos en una base de datos de Access \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)