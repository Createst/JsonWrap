package com.wj.controller;

import java.lang.reflect.Field;
import java.util.Collection;

/**
 * Created by 王军 on 2016/4/3.
 * function:将实现Collection的集合类中的对象转为JSON对象字符串
 *
 */
public class JsonWrap {
    private static StringBuilder stringBuilder;
    private static Boolean flag = false;
    private static String message;
    /**
     *
     * @param collection 将要转为JSON字符串数组的集合，该集合必须是Collection的实现类
     * @return 返回JSON对象字符数组
     */
    public static String toJsonString(Collection<?> collection)
    {
        if(collection == null)
        {
            throw new RuntimeException("参数不能为null");
        }
        stringBuilder = new StringBuilder();
        stringBuilder.append("[");
        int size = collection.size();
        int count = 0;
        for(Object o:collection)
        {
            count++;
            Field[] fields = o.getClass().getDeclaredFields();
            int length = fields.length;
            String str = "{";
            for(int i = 0;i<length;++i)
            {
                Field f = fields[i];
                if(!f.isAccessible())
                {
                    f.setAccessible(true);
                }
                    String name = f.getName();
                    Object value = null;
                try {
                    value = f.get(o);
                } catch (IllegalAccessException e) {
                    e.printStackTrace();
                }
                if(i == length-1)
                    {
                        str +=  "\""+name+"\":\"" + value + "\"" ;
                    }else{
                        str +=  "\""+name+"\":\"" + value + "\"" +",";
                    }
            }
            str += (count == size)?"}]":"},";
            stringBuilder.append(str);
        }
        return stringBuilder.toString();
    }
    /**
     *
     * @param o 将要转为JSON字符串的对象。
     * @return 返回JSON对象字符串
     */
    public static String toJsonString2(Object o)
    {
        if(o == null)
        {
            throw new RuntimeException("参数不能为null");
			return null；
        }
		if( o instance of collection || o instance of map)
		{
			throw new RuntimeException("参数不能为集合");
			return null；
		}
        stringBuilder = new StringBuilder();
        Field[] fields = o.getClass().getDeclaredFields();
        int length = fields.length;
        String str = "{";
        for(int i = 0;i<length;++i)
        {
            Field f = fields[i];
            if(!f.isAccessible())
            {
                f.setAccessible(true);
            }

            String name = f.getName();
            Object value = null;
            try {
                value = f.get(o);
            } catch (IllegalAccessException e) {
                e.printStackTrace();
            }
            if(i == length-1)
            {
                str +=  "\""+name+"\":\"" + value + "\"}" ;
            }else{
                str +=  "\""+name+"\":\"" + value + "\"" +",";
            }
        }
       stringBuilder.append(str);
        return stringBuilder.toString();
    }

    /**
     *
     * @param b 用于向前台发送的标志位
     * @param m 信息
     * @return 向前台发送的判断信息
     */
    public static String wrap(Boolean b,String m)
    {
        flag = b;
        message = m;
        return "{\"flag\":"+flag+""+","+"\"message\":\""+message+"\"}";
    }
}
