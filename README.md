# ProxyModel
����ģʽ��Proxy����Ϊ���������ṩһ�ִ����Կ��ƶ��������ķ��ʡ�
��һ�»������롣
abstract class Subject{
 public abstract void Request();
}
class RealSubject extends Subject{
 @Override
 public void Request(){
  //��ʵ������
 }
}
class Proxy extends Subject{
 private RealSubject realSubject;
 @Override
 public void Request(){
  if(realSubject == null){
    realSubject = new RealSubject();
  }
  realSubject.Request();
 }
}
�ͻ��˴���
class MainActivity extends Activity{
 public void onCreate(){
  Proxy proxy = new Proxy();
  proxy.Request();
 }
}
�������ٸ����ӣ�Ӧ��һ�´���ģʽ������AͬѧҪ��Cͬѧ���������Cͬѧ����ʶAͬѧ����ô���أ���ôBͬѧ�ͳ����ˡ�B��A�Ǻ����ѣ�B��CҲ��ʶ����ôAҪ��C���������ͨ��B��ʵ���������
������������ԭ����Խӿڱ�̡�
package com.abings.proxymodel.Proxy;

/**
 * Created by Shuwen on 2016/8/31.
 */
public interface GiftSubject {
    void giveFloors();
    void giveDolls();
    void giveLove();
}
�����ǿ��ŷ��ԭ������������Ķ���
package com.abings.proxymodel.Proxy;

import android.content.Context;
import android.widget.Toast;

/**
 * Created by Shuwen on 2016/8/31.
 */
public class RealSubjectPersonA implements GiftSubject {

    private String name;
    private Context context;
    public RealSubjectPersonA(String name,Context context){
        this.name = name;
        this.context = context;
    }

    @Override
    public void giveFloors() {
        Toast.makeText(context, "A������"+name+"С��һ������", Toast.LENGTH_SHORT).show();
    }

    @Override
    public void giveDolls() {
        Toast.makeText(context, "A������"+name+"С��һ������ܡ�", Toast.LENGTH_SHORT).show();
    }

    @Override
    public void giveLove() {
        Toast.makeText(context, "A������"+name+"С���ﰮ�⡣", Toast.LENGTH_SHORT).show();
    }
}
�������Ǵ������
package com.abings.proxymodel.Proxy;

import android.content.Context;

/**
 * Created by Shuwen on 2016/8/31.
 */
public class ProxyPersonB implements GiftSubject {
    private RealSubjectPersonA realSubjectPersonA;
    public ProxyPersonB(PersonC personC,Context context){
        if (realSubjectPersonA == null){
            realSubjectPersonA = new RealSubjectPersonA(personC.getName(),context);
        }
    }

    @Override
    public void giveFloors() {
        realSubjectPersonA.giveFloors();
    }

    @Override
    public void giveDolls() {
        realSubjectPersonA.giveDolls();
    }

    @Override
    public void giveLove() {
        realSubjectPersonA.giveLove();
    }
}
����ǰ���UMLͼ��Ƴ����Ĵ��룬���׶�����˳����ߴ�ң�׷Ů���Ӳ��ô���ģʽ�����յĽ���Ǵ����Ǹ��˻�ɹ�׷���֡��಻���ԵĽ�֣���԰������Ҫ���ڱ���Ȼֻ�е���������������Գ����Ҳ���������������ˡ���





