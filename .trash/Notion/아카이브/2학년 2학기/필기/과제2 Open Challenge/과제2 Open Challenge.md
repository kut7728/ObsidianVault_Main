---
강의 리스트:
  - "[[자바 프로그래밍 입문]]"
---
```Java
import javax.swing.*;
import javax.swing.event.ChangeEvent;
import javax.swing.event.ChangeListener;

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;
import java.awt.event.KeyAdapter;
import java.awt.event.KeyEvent;
import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;
import java.awt.event.MouseMotionListener;
import java.util.Vector;
import java.awt.*;

class CenterPanel extends JPanel{
	
	private ImageIcon []images= {
			new ImageIcon("/Users/nelime/Desktop/eclipse-workspace/OpenChallenge11/src/dog.jpg"),
			new ImageIcon("/Users/nelime/Desktop/eclipse-workspace/OpenChallenge11/src/fantasy.jpg"),
			new ImageIcon("/Users/nelime/Desktop/eclipse-workspace/OpenChallenge11/src/foliage.jpg")
	};
	private static Vector<ImageIcon> v=new Vector<ImageIcon>();
	private static JLabel jl;
	private static int idx=0;
	
	CenterPanel(){
		setLayout(new FlowLayout(FlowLayout.CENTER));
		
		for(int i=0;i<images.length;i++) {
			v.add(images[i]);
		}
		
		jl=new JLabel(v.get(0));
		add(jl);
	}
	
	static void change_Left() {
		idx = idx-1 < 0 ? v.size() - 1 : idx - 1;
		jl.setIcon(v.get(idx));
	}
	
	static void change_Right() {
		idx = idx+1 == v.size() ? 0 : idx + 1;
		jl.setIcon(v.get(idx));
	}
}

class SouthPanel extends JPanel{
	
	private JButton []jbtn=new JButton[2];
	
	SouthPanel(){
		setLayout(new FlowLayout(FlowLayout.CENTER));
		setBackground(Color.GRAY);
		
		jbtn[0]=new JButton(new ImageIcon("/Users/nelime/Desktop/eclipse-workspace/OpenChallenge11/src/left.png"));
		jbtn[1]=new JButton(new ImageIcon("/Users/nelime/Desktop/eclipse-workspace/OpenChallenge11/src/right.png"));
		
		add(jbtn[0]);
		add(jbtn[1]);
		
		jbtn[0].addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				CenterPanel.change_Left();
			}
		});
		
		jbtn[1].addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				CenterPanel.change_Right();
			}
		});
	}
}

public class MyFrame extends JFrame{
	
	MyFrame(){
		setTitle("11장 Open Challenge");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		Container c = getContentPane();
		c.setLayout(new BorderLayout());
	
		c.add(new CenterPanel(),BorderLayout.CENTER);
		c.add(new SouthPanel(),BorderLayout.SOUTH);
		
		setSize(300, 300);
		setVisible(true);
		
		c.setFocusable(true);
		c.requestFocus();
	}
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		new MyFrame();
	}

}
```

  

![[CleanShot_2023-06-07_at_23.10.342x.png]]

![[CleanShot_2023-06-07_at_23.10.442x.png]]

![[CleanShot_2023-06-07_at_23.10.482x.png]]

  

  

## 11장 연습문제 10번

```Java
import javax.swing.*; 
import javax.swing.event.ChangeEvent;
import javax.swing.event.ChangeListener;
import java.awt.*; 
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;
import java.awt.event.KeyAdapter;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import java.awt.event.MouseAdapter;
import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;
import java.awt.event.MouseMotionListener;
import java.util.Vector;
import java.awt.*;

public class MyFrame extends JFrame{
	
	private static JLabel []jl=new JLabel[10];
	private static int click_Cnt=0;
	
	static void setLabel(Container c) {
		for(int i=0; i<jl.length; i++) {
			jl[i]=new JLabel(Integer.toString(i));
			jl[i].setSize(30,30);
			jl[i].setFont(new Font("Arial",Font.PLAIN,30));
			jl[i].setForeground(Color.PINK);
			
			
			int x=(int)(Math.random()*300+20);
			int y=(int)(Math.random()*300+20);
			jl[i].setLocation(x,y);
			c.add(jl[i]);
		}
	}
	
	static void reSetLabel(Container c) {
		click_Cnt=0;
		
		for(int i=0;i<jl.length;i++) {
			jl[i].setSize(30,30);
			int x=(int)(Math.random()*300+20);
			int y=(int)(Math.random()*300+20);
			jl[i].setLocation(x,y);
		}
	}
	
	MyFrame(){
		setTitle("11장 실습문제");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		Container c = getContentPane();
		c.setLayout(null);

		setLabel(c);
		
		for(int i=0;i<jl.length;i++) {
			jl[i].addMouseListener(new MouseAdapter() {
				public void mousePressed(MouseEvent e) {
					// TODO Auto-generated method stub
					JLabel la=(JLabel)e.getSource();
					if(click_Cnt==Integer.parseInt(la.getText())) {
						la.setSize(0,0);
						click_Cnt++;
						if(click_Cnt==10) {
							reSetLabel(c);
						}	
					}
				}
			});
		}
		
		setSize(400, 400);
		setVisible(true);
		
		c.setFocusable(true);
		c.requestFocus();
	}
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		new MyFrame();
	}

}
```

  

![[CleanShot_2023-06-07_at_23.15.562x.png]]

![[CleanShot_2023-06-07_at_23.16.092x.png]]