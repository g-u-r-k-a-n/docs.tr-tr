---
title: Dosyaları ve Dizinleri Düzenleme
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
ms.openlocfilehash: 83dc6ce0d29c1c368c36b51fc84ecad34d72e01f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333802"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="5d802-102">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="5d802-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="5d802-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5d802-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="5d802-104">It describes how to create a small application that lists and examines text files in a directory.</span><span class="sxs-lookup"><span data-stu-id="5d802-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="5d802-105">For each selected text file, the application provides file attributes and the first line of content.</span><span class="sxs-lookup"><span data-stu-id="5d802-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="5d802-106">There is an option to write information to a log file.</span><span class="sxs-lookup"><span data-stu-id="5d802-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="5d802-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5d802-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="5d802-108">Daha fazla bilgi edinmek için bkz. <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="5d802-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="5d802-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span><span class="sxs-lookup"><span data-stu-id="5d802-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="5d802-110">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5d802-110">To create the project</span></span>  
  
1. <span data-ttu-id="5d802-111">On the **File** menu, click **New Project**.</span><span class="sxs-lookup"><span data-stu-id="5d802-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="5d802-112">The **New Project** dialog box appears.</span><span class="sxs-lookup"><span data-stu-id="5d802-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="5d802-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span><span class="sxs-lookup"><span data-stu-id="5d802-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="5d802-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span><span class="sxs-lookup"><span data-stu-id="5d802-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="5d802-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span><span class="sxs-lookup"><span data-stu-id="5d802-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="5d802-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span><span class="sxs-lookup"><span data-stu-id="5d802-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="5d802-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span><span class="sxs-lookup"><span data-stu-id="5d802-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="5d802-118">Denetim</span><span class="sxs-lookup"><span data-stu-id="5d802-118">Control</span></span>|<span data-ttu-id="5d802-119">Özellik</span><span class="sxs-lookup"><span data-stu-id="5d802-119">Property</span></span>|<span data-ttu-id="5d802-120">Değer</span><span class="sxs-lookup"><span data-stu-id="5d802-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="5d802-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="5d802-121">**ListBox**</span></span>|<span data-ttu-id="5d802-122">**Ad**</span><span class="sxs-lookup"><span data-stu-id="5d802-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="5d802-123">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="5d802-123">**Button**</span></span>|<span data-ttu-id="5d802-124">**Ad**</span><span class="sxs-lookup"><span data-stu-id="5d802-124">**Name**</span></span><br /><br /> <span data-ttu-id="5d802-125">**Metin**</span><span class="sxs-lookup"><span data-stu-id="5d802-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="5d802-126">**Browse**</span><span class="sxs-lookup"><span data-stu-id="5d802-126">**Browse**</span></span>|  
    |<span data-ttu-id="5d802-127">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="5d802-127">**Button**</span></span>|<span data-ttu-id="5d802-128">**Ad**</span><span class="sxs-lookup"><span data-stu-id="5d802-128">**Name**</span></span><br /><br /> <span data-ttu-id="5d802-129">**Metin**</span><span class="sxs-lookup"><span data-stu-id="5d802-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="5d802-130">**Examine**</span><span class="sxs-lookup"><span data-stu-id="5d802-130">**Examine**</span></span>|  
    |<span data-ttu-id="5d802-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="5d802-131">**CheckBox**</span></span>|<span data-ttu-id="5d802-132">**Ad**</span><span class="sxs-lookup"><span data-stu-id="5d802-132">**Name**</span></span><br /><br /> <span data-ttu-id="5d802-133">**Metin**</span><span class="sxs-lookup"><span data-stu-id="5d802-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="5d802-134">**Save Results**</span><span class="sxs-lookup"><span data-stu-id="5d802-134">**Save Results**</span></span>|  
    |<span data-ttu-id="5d802-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="5d802-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="5d802-136">**Ad**</span><span class="sxs-lookup"><span data-stu-id="5d802-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="5d802-137">To select a folder, and list files in a folder</span><span class="sxs-lookup"><span data-stu-id="5d802-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="5d802-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span><span class="sxs-lookup"><span data-stu-id="5d802-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="5d802-139">The Code Editor opens.</span><span class="sxs-lookup"><span data-stu-id="5d802-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="5d802-140">Add the following code to the `Click` event handler.</span><span class="sxs-lookup"><span data-stu-id="5d802-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="5d802-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span><span class="sxs-lookup"><span data-stu-id="5d802-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="5d802-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span><span class="sxs-lookup"><span data-stu-id="5d802-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="5d802-143">Add the following `ListFiles` method.</span><span class="sxs-lookup"><span data-stu-id="5d802-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="5d802-144">This code first clears the **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="5d802-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="5d802-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span><span class="sxs-lookup"><span data-stu-id="5d802-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="5d802-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span><span class="sxs-lookup"><span data-stu-id="5d802-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="5d802-147">In this example, only files that have the extension .txt are returned.</span><span class="sxs-lookup"><span data-stu-id="5d802-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="5d802-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="5d802-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="5d802-149">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5d802-149">Run the application.</span></span> <span data-ttu-id="5d802-150">Click the **Browse** button.</span><span class="sxs-lookup"><span data-stu-id="5d802-150">Click the **Browse** button.</span></span> <span data-ttu-id="5d802-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span><span class="sxs-lookup"><span data-stu-id="5d802-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="5d802-152">The `ListBox` contains a list of .txt files in the selected folder.</span><span class="sxs-lookup"><span data-stu-id="5d802-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="5d802-153">Stop running the application.</span><span class="sxs-lookup"><span data-stu-id="5d802-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="5d802-154">To obtain attributes of a file, and content from a text file</span><span class="sxs-lookup"><span data-stu-id="5d802-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="5d802-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span><span class="sxs-lookup"><span data-stu-id="5d802-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="5d802-156">Add the following code to the `Click` event handler.</span><span class="sxs-lookup"><span data-stu-id="5d802-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="5d802-157">The code verifies that an item is selected in the `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="5d802-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="5d802-158">It then obtains the file path entry from the `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="5d802-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="5d802-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span><span class="sxs-lookup"><span data-stu-id="5d802-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="5d802-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span><span class="sxs-lookup"><span data-stu-id="5d802-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="5d802-161">This method returns a string that contains file information.</span><span class="sxs-lookup"><span data-stu-id="5d802-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="5d802-162">The file information appears in a **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="5d802-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="5d802-163">Add the following `GetTextForOutput` method.</span><span class="sxs-lookup"><span data-stu-id="5d802-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="5d802-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span><span class="sxs-lookup"><span data-stu-id="5d802-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="5d802-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="5d802-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="5d802-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="5d802-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="5d802-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="5d802-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="5d802-168">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5d802-168">Run the application.</span></span> <span data-ttu-id="5d802-169">Click **Browse**, and browse to a folder that contains .txt files.</span><span class="sxs-lookup"><span data-stu-id="5d802-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="5d802-170">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d802-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="5d802-171">Select a file in the `ListBox`, and then click **Examine**.</span><span class="sxs-lookup"><span data-stu-id="5d802-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="5d802-172">A `MessageBox` shows the file information.</span><span class="sxs-lookup"><span data-stu-id="5d802-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="5d802-173">Stop running the application.</span><span class="sxs-lookup"><span data-stu-id="5d802-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="5d802-174">To add a log entry</span><span class="sxs-lookup"><span data-stu-id="5d802-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="5d802-175">Add the following code to the end of the `examineButton_Click` event handler.</span><span class="sxs-lookup"><span data-stu-id="5d802-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="5d802-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span><span class="sxs-lookup"><span data-stu-id="5d802-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="5d802-177">The text of the log entry is set to the current date and time followed by the file information.</span><span class="sxs-lookup"><span data-stu-id="5d802-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="5d802-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span><span class="sxs-lookup"><span data-stu-id="5d802-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="5d802-179">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5d802-179">Run the application.</span></span> <span data-ttu-id="5d802-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span><span class="sxs-lookup"><span data-stu-id="5d802-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="5d802-181">Verify that the log entry is written to the `log.txt` file.</span><span class="sxs-lookup"><span data-stu-id="5d802-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="5d802-182">Stop running the application.</span><span class="sxs-lookup"><span data-stu-id="5d802-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="5d802-183">To use the current directory</span><span class="sxs-lookup"><span data-stu-id="5d802-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="5d802-184">Create an event handler for `Form1_Load` by double-clicking the form.</span><span class="sxs-lookup"><span data-stu-id="5d802-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="5d802-185">Add the following code to the event handler.</span><span class="sxs-lookup"><span data-stu-id="5d802-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="5d802-186">This code sets the default directory of the folder browser to the current directory.</span><span class="sxs-lookup"><span data-stu-id="5d802-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="5d802-187">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5d802-187">Run the application.</span></span> <span data-ttu-id="5d802-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span><span class="sxs-lookup"><span data-stu-id="5d802-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="5d802-189">Stop running the application.</span><span class="sxs-lookup"><span data-stu-id="5d802-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="5d802-190">To selectively enable controls</span><span class="sxs-lookup"><span data-stu-id="5d802-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="5d802-191">Add the following `SetEnabled` method.</span><span class="sxs-lookup"><span data-stu-id="5d802-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="5d802-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="5d802-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="5d802-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span><span class="sxs-lookup"><span data-stu-id="5d802-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="5d802-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span><span class="sxs-lookup"><span data-stu-id="5d802-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="5d802-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span><span class="sxs-lookup"><span data-stu-id="5d802-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="5d802-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span><span class="sxs-lookup"><span data-stu-id="5d802-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="5d802-197">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5d802-197">Run the application.</span></span> <span data-ttu-id="5d802-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="5d802-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="5d802-199">Full example using My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="5d802-199">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="5d802-200">Following is the complete example.</span><span class="sxs-lookup"><span data-stu-id="5d802-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="5d802-201">Full example using System.IO</span><span class="sxs-lookup"><span data-stu-id="5d802-201">Full example using System.IO</span></span>  

 <span data-ttu-id="5d802-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span><span class="sxs-lookup"><span data-stu-id="5d802-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="5d802-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d802-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="5d802-204">İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="5d802-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
