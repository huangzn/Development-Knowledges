   

# SpringMVC接收前台传递过来的值的方法 #

## 之前控制器方法获得前台传来的值有三种方式： ##
**1. 通过HttpServletRequest：**

    @RequestMapping(value="/index1")
    public String helloaction1(HttpServletRequest request){
         System.out.println(request.getParameter("nnn"));  //获得前台name为nnn的元素的值
         return "index";
    }
 
**2. 通过参数名获得：**

    @RequestMapping(value="/index1")
    public String helloaction1(String nnn){      //这里名字要与前端元素名字一致才能获得
         System.out.println(nnn);    
         return "index";
    }

**3. 通过@RequestParam注解获得：**

    @RequestMapping(value="/index")
    public String helloaction(@RequestParam(value="nnn",required=false)String nnn1, Model model){  //nnn要与前端一致，在此处可以理解为参数nnn1的别名
         System.out.println(nnn1);
         model.addAttribute("hello", "这是用action传过来的值："+nnn1);
         return "index";
    }

**4. SpringMvc还能通过将vo作为参数获得vo的各个属性：**

    @RequestMapping(value="/index2")
    public String helloaction2(User user){      
         System.out.println(user.getAccount());
         System.out.println(user.getPassword());
         return "index";
    } 

使用对象进行获取数据的时候要注意，前端页面的元素name属性要与vo的各个属性名字一致


[来自](https://blog.csdn.net/w405722907/article/details/73543497 "blog.csdn.net/w405722907/article/details/73543497")
