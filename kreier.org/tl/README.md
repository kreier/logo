# Logo for kreier.org/tl

The Web version of the timeline. Background color: #324167

## Grid parameters

For the logo it is the regular 1024x1024 shape. The logo fits inside 75% in the center, which is 768 pixels and 128 pixels border left and right. The logo itself fits on a 4x4 grid, which divides the central 768 pixels into four 192 pixel wide squares.

The edge points horizontally and vertically are therefore:

- 128
- 320
- 512
- 704
- 896

As done in below image:

## Rendered images

<img src="TL.png" width="49%"> <img src="TL_gradient.jpg" width="49%"> 

## 20 pixel space between

If the block size is just 177 and the space between is 20, we get new grid parameters:

- 128
- 305 - 325
- 502 - 522
- 699 - 719
- 896

## 64 pixel space between

- 128 | 272 - 336 | 480 - 544 | 688 - 752 | 896
- 128 - 272 | 336 - 480 | 544 - 688 | 752 - 896
- 272 - 336
- 480 - 544
- 688 - 752
- 896

## 68 pixels space between - almost 50% of letter width 141 pixels, we get

- 128 - 269
- 337 - 478
- 546 - 687
- 755 - 896

## Visualize with AppScript in Google Sheets

The varying width of space for the 4x4 grid was best visualized with 3 lines between them and adjusting them. 50% looks ok, but gives no rational ratio. So the 100/50 ratio from Google sheets was translated to 141/68. Here is the script:

``` javascript
function adjustGridSizePrompt() {
  var ui = SpreadsheetApp.getUi();
  var response = ui.prompt("Enter the size (pixels):");
  var value = parseInt(response.getResponseText(), 10);
  
  if (!isNaN(value)) {
    var sheet = SpreadsheetApp.getActiveSheet();
    var cols = [2, 4, 6];
    var rows = [2, 4, 6];
    
    cols.forEach(function(col, i) {
      sheet.setColumnWidth(col, value);
      sheet.setRowHeight(rows[i], value);
    });
  }
}
```
