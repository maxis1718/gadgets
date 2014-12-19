- Save as a browser bookmark

  ```
javascript:((function(){ var supported_exts = ['png', 'jpg', 'jpeg', 'gif', 'bmp']; $.each($('table.files').find('tr'), function(i, obj){ var img_url = $(obj).find('td.content').find('a').attr('href'); if(img_url === undefined){ return true; } var ext = (/[.]/.exec(img_url)) ? /[^.]+$/.exec(img_url) : undefined; if(ext === undefined){ return true; } if( $.inArray(ext[0].toLowerCase(), supported_exts) != -1) { var img_raw = img_url+'?raw=true'; var tr = $('<tr/>'); var td = $('<td/>').attr('colspan',4).appendTo(tr); var img = $('<img/>').attr('src', img_raw).appendTo(td); $(obj).after(tr); } }); })());
  ```

- Raw code:

  ```
var supported_exts = ['png', 'jpg', 'jpeg', 'gif', 'bmp'];
$.each($('table.files').find('tr'), function(i, obj){
    var img_url = $(obj).find('td.content').find('a').attr('href');
    if(img_url === undefined){ return true; }
    var ext = (/[.]/.exec(img_url)) ? /[^.]+$/.exec(img_url) : undefined;
    if(ext === undefined){ return true; }
    if( $.inArray(ext[0].toLowerCase(), supported_exts) != -1)
    {
            var img_raw = 'https://raw.githubusercontent.com' + img_url.replace('/blob/','/');
            var tr = $('<tr/>');
            var td = $('<td/>').attr('colspan',4).appendTo(tr);
            var img = $('<img/>').attr('src', img_raw).appendTo(td);
            $(obj).after(tr);
    }
});
  ```


