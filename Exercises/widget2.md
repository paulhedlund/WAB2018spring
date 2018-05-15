# Custom Widget #2 - Zoom to Minnesota County
___

1)	Start by going through steps #1 to #13 in **The Terrible Widget** except call it the widget **CountyWidget**.  Select a different Icon as well.

2)	Add AGO map to the sample config.  This is done by navigating to **\\client\stemapp\sample-configs**. Open the config-demo.json file and go to **map -> itemId** and change the Web Map ID to 

    ```
    bbd3477a3f0944a48881f681a8530be2
    ```

    ![](img/ex1/widg2_pc1.png)

3)	This widget will not require some template files.  Therefore, remove the **config.json** file and **nls** folder.

    ![](img/ex1/widg2_pc2.png)

4)	Edit the **Manifest.json** file to not include some properties.  Have the parameters similar to what is seen below.

    ![](img/ex1/widg2_pc3.png)
    
5)	This widget will require some HTML syntax containing some DOJO/DIJIT widgets. First, remove any existing text in the **widget.html** file.  Then, copy the text below. 

    ```
    <div>
    <span class="sectionTitles">Minnesota County List</span>
    <div id="filterBlock">
      <table width="100%">
        <tr>
    <td class=tableAlignLeft><select dojotype="dijit/form/FilteringSelect" data-dojo-props="id:'MNcountylist', autoComplete:false, value:'', placeHolder: 'Select county ...'" required="false" />
    </tr>
          </table>
        </div>
        <div id="buttonBlock" style=”margin-top:10px;”>
          <table width=”100%”>
            <tr>
              <td style="text-align:center;"><div class="jimu-btn" data-dojo-attach-point="btnVote" data-dojo-attach-event="click:_ZoomCounty">Zoom to County</div></td>
            </tr>
          </table>
        </div>
    </div>
    ```
    
6)	Now let’s spend some time adding code to the **widget.js** file.  This file will contain the most logic of any file for the widget.  First un-comment the **postCreate** and **startup** event functions.  Remove all other commented functions including **onOpen**, **onClose**, etc.  These events will not be used for this widget.

    ![](img/ex1/widg2_pc4.png)
    
7)	Part of the ArcGIS JavaScript API framework is something called AMD (Asynchronous Module Definition).  Part of the AMD process is adding ESRI libraries ins declarative process.  Add the following code to the top of the **widget.js** file underneath the ‘jimu/BaseWidget’ item in define.
