---
title: "Ejemplo de demostración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: be42ed54e2c245a47e885fe8310c106c27ea82b2
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="demo-sample"></a>Ejemplo de demostración
Este procedimientos siguientes muestran cómo crear el ejemplo para [Tutorial: analizar código de C/C ++ en previsión de defectos](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Crean los procedimientos:  
  
-   Un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución denominada CppDemo.  
  
-   Un proyecto de biblioteca estática denominado CodeDefects.  
  
-   Un proyecto de biblioteca estática denominado Annotations.  
  
 Los procedimientos también proporcionan el código para los archivos de encabezado y .cpp para las bibliotecas estáticas.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Crear la solución CppDemo y el proyecto CodeDefects  
  
1.  Haga clic en el **archivo** menú, elija **New**y, a continuación, haga clic en **nuevo proyecto**.  
  
2.  En el **tipos de proyecto** lista de árbol, expanda si Visual C++ no es el idioma predeterminado en VS **otros lenguajes**.  
  
3.  Expanda **Visual C++**y, a continuación, haga clic en **General**.  
  
4.  En **plantillas**, haga clic en **proyecto vacío de servidor**.  
  
5.  En el **nombre** cuadro de texto, escriba **CodeDefects**.  
  
6.  Seleccione el **crear directorio para la solución** casilla de verificación.  
  
7.  En el **nombre de la solución** cuadro de texto, escriba **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Configurar el proyecto CodeDefects como una biblioteca estática  
  
1.  En el Explorador de soluciones, haga clic en **CodeDefects** y, a continuación, haga clic en **propiedades**.  
  
2.  Expanda **propiedades de configuración** y, a continuación, haga clic en **General**.  
  
3.  En el **General** , seleccione el texto de la columna junto a **extensión de destino**y, a continuación, escriba **.lib**.  
  
4.  En **valores predeterminados del proyecto**, haga clic en la columna junto a **tipo de configuración**y, a continuación, haga clic en **biblioteca estática (.lib)**.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Agregue el archivo de encabezado y código fuente para el proyecto CodeDefects  
  
1.  En el Explorador de soluciones, expanda **CodeDefects**, haga clic en **archivos de encabezado**, haga clic en **agregar**y, a continuación, haga clic en **nuevo elemento**.  
  
2.  En el **Agregar nuevo elemento** cuadro de diálogo, haga clic en **código**y, a continuación, haga clic en **archivo de encabezado (. h)**.  
  
3.  En el **nombre** , escriba **Bug.cpp** y, a continuación, haga clic en **agregar**.  
  
4.  Copie el código siguiente y péguelo en el **Bug.cpp** un archivo en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
    ```cpp
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  En el Explorador de soluciones, haga clic en **archivos de código fuente**, seleccione **New**y, a continuación, haga clic en **nuevo elemento**.  
  
6.  En el **Agregar nuevo elemento** cuadro de diálogo, haga clic en **archivo C++ (.cpp)**  
  
7.  En el **nombre** , escriba **Bug.cpp** y, a continuación, haga clic en **agregar**.  
  
8.  Copie el código siguiente y péguelo en el archivo Bug.h del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
    ```cpp
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Haga clic en el **archivo** menú y, a continuación, haga clic en **guardar todo**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Agregar el proyecto Annotations y configurarlo como una biblioteca estática  
  
1.  En el Explorador de soluciones, haga clic en **CppDemo**, seleccione **agregar**y, a continuación, haga clic en **nuevo proyecto**.  
  
2.  En el **Agregar nuevo proyecto** diálogo cuadro, expanda Visual C++, haga clic en **General**y, a continuación, haga clic en **proyecto vacío de servidor**.  
  
3.  En el **nombre** cuadro de texto, escriba **anotaciones**y, a continuación, haga clic en **agregar**.  
  
4.  En el Explorador de soluciones, haga clic en **anotaciones** y, a continuación, haga clic en **propiedades**.  
  
5.  Expanda **propiedades de configuración** y, a continuación, haga clic en **General**.  
  
6.  En el **General** , seleccione el texto de la columna junto a **extensión de destino**y, a continuación, escriba **.lib**.  
  
7.  En **valores predeterminados del proyecto**, haga clic en la columna junto a **tipo de configuración**y, a continuación, haga clic en **biblioteca estática (.lib)**.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Agregue el archivo de encabezado y el archivo de código fuente al proyecto anotaciones  
  
1.  En el Explorador de soluciones, expanda **anotaciones**, haga clic en **archivos de encabezado**, haga clic en **agregar**y, a continuación, haga clic en **nuevo elemento**.  
  
2.  En el **Agregar nuevo elemento** cuadro de diálogo, haga clic en **archivo de encabezado (. h)**.  
  
3.  En el **nombre** , escriba **annotations.h** y, a continuación, haga clic en **agregar**.  
  
4.  Copie el código siguiente y péguelo en el **annotations.h** un archivo en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  En el Explorador de soluciones, haga clic en **archivos de código fuente**, seleccione **New**y, a continuación, haga clic en **nuevo elemento**.  
  
6.  En el **Agregar nuevo elemento** cuadro de diálogo, haga clic en **código** y, a continuación, haga clic en **archivo C++ (.cpp)**  
  
7.  En el **nombre** , escriba **annotations.cpp** y, a continuación, haga clic en **agregar**.  
  
8.  Copie el código siguiente y péguelo en el **annotations.cpp** un archivo en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Haga clic en el **archivo** menú y, a continuación, haga clic en **guardar todo**.