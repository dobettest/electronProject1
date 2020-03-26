var reg = RegExp(/\W/)
      if (d === "＝") {
        if (currentValue.length == 0)
          globalData.currentValue = "0"
        let v = globalData.currentValue.split(reg)
        console.log([...v])
        $(".result > span").text(123)
      }
      if (currentValue.length > 0 && d.match(reg) && currentValue[currentValue.length - 1].match(reg)) {
        return
      }
      else {
        currentValue = currentValue.length > 0 ? currentValue + d : d
        globalData.currentValue = currentValue
      }
      $('input').val(globalData.currentValue)
      console.log(globalData.currentValue)


      /*function render() {
      var els = $(".btn_item");
      var data = ["%", "CE", "c","退格","1/x","x^2","∑","➗","7","8","9","X","4","5","6","-","1","2","3","+","+/-","0",".","="]
        els.get().forEach((v, i) => {
          console.log(v)
          $(v).attr("data-a", data[i])
        })
      console.log(els)
    }*/

    meta第二行的限制有问题。第一个报错只你把unsafe-eval作为一个指令名是不对的，它是src类型资源的一个限制值；第二个报错指你的script-src中没有unsafe-eval这个值。
应改为：


<meta http-equiv="Content-Security-Policy" content="default-src 'self' data: gap: https://ssl.gstatic.com; style-src 'self' 'unsafe-inline'; media-src *;connect-src *;script-src * 'unsafe-inline' 'unsafe-eval';">