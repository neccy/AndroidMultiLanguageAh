# AndroidMultiLanguage
记APP实现多语言（国际化）过程，兼容Android 8.0
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;示例项目的效果图
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;        ![这里写图片描述](http://oxmx4a7d0.bkt.clouddn.com/blog_finddreams_language20171107.gif)

-------------------------------------------------------------------------------------------------
操作步骤：

           1. 将我最新发布作为依赖；
					 
           2. 项目应用的Application的onCreate方法里进行注册：   MultiLanguageUtil.init(this);
					 
           3. 项目基类重写绑定上下文的方法:
            @Override
    protected void attachBaseContext(Context newBase) {
        super.attachBaseContext(MultiLanguageUtil.attachBaseContext(newBase));
    }
		
            4. 通过应用内选择的语言进行语言重置：
     /**
     * 设置应用语言
     */
    public static void setLocalLanguage(Activity context) {
        int language = spLanguage.getInt(Constants.LANGUAGE, 0);
        switch (language) {
            case 0:
                MultiLanguageUtil.getInstance().updateLanguage(LanguageType.LANGUAGE_CHINESE_SIMPLIFIED);
                break;
            case 1:
                MultiLanguageUtil.getInstance().updateLanguage(LanguageType.LANGUAGE_EN);
                break;
        }
        Intent intent = new Intent(x.app(), HomeActivity.class);
        intent.setFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
        context.startActivity(intent);
    }
		
   如果大家实在不懂的， 可以参考原创链接：https://blog.csdn.net/finddreams/article/details/78470768?utm_source=tuicool&utm_medium=referral
