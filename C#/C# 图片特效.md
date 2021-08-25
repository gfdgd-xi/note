# 摘要
大家用过图片修改软件吧，很多功能可以让你惊叹，这里给出少部分图片特效的方法供大家调用（本人小白，代码方面可能有问题，请各位大神见谅）


# 图片特效的代码（提供的是命名空间）

```csharp
/*
 *********************************************************************************************************************************
 * Bug 已知列表：                                                                                                                *
 *     1、修复在旋转图片操作时，原图也会被修改的情况，波及范围：旋转180度、逆时针旋转90度、顺时针旋转90度、垂直旋转、水平旋转    *
 *     （时间：2020-8-23 16:12:23）                                                                                              *
 *     解决方法：可先用“旋转任意度数”方法旋转图片，旋转可能有损或在以相反操作操作图片，恢复初始状态。                          *
 *     原因：未知。                                                                                                              *
 *     原代码（部分）：                                                                                                          *
 *     /// <summary>                                                                                                             *
 *      /// 图片顺时针旋转90°                                                                                                   *
 *      /// </summary>                                                                                                           *
 *      /// <param name="yuan">要旋转的图片</param>                                                                              *
 *      /// <returns>旋转后的图片</returns>                                                                                      *
 *      public Bitmap 顺时针旋转90度(Bitmap yuan)                                                                                *
 *      {                                                                                                                        *
 *          try                                                                                                                  *
 *          {                                                                                                                    *
 *              yuan.RotateFlip(RotateFlipType.Rotate270FlipXY);                                                                 *
 *          }                                                                                                                    *
 *          catch { } // 忽略错误                                                                                                *
 *          return yuan; // 返回结果                                                                                             *
 *      }                                                                                                                        *
 *********************************************************************************************************************************
 */
/// <summary>
/// 图片修改
/// </summary>
namespace 修改图片
{
    /// <summary>
    /// 图片颜色基本操作
    /// </summary>
    class 颜色
    {
        /// <summary>
        /// 将图片指定的颜色替换为透明颜色
        /// </summary>
        /// <param name="yuan">原来的图片</param>
        /// <param name="ti">要替换的颜色</param>
        /// <returns>替换后的结果</returns>
        public Bitmap 将指定颜色替换为透明(Bitmap yuan, Color ti)
        {
            yuan.MakeTransparent(ti);
            return yuan;
        }
        /// <summary>
        /// 将A颜色替换为B颜色
        /// </summary>
        /// <param name="yuan">要修改的图片</param>
        /// <param name="a">要替换的颜色</param>
        /// <param name="b">要替换成的颜色</param>
        /// <returns>替换后结果的图片</returns>
        public Bitmap 替换颜色(Bitmap yuan, Color a, Color b)
        {
            for (int x = 1; x < yuan.Width; x++) // 将每个x轴都循环一遍
            {
                for (int y = 1; y < yuan.Height; y++) // 将每个y轴循环一遍
                {
                    if (yuan.GetPixel(x, y).ToArgb() == a.ToArgb()) // 将颜色转为32位Argb结构，如果值相等，就
                    {
                        yuan.SetPixel(x, y, b); // 将指定x轴和y轴设定为指定颜色
                    }
                }
            }
            return yuan;
        }
    }
    /// <summary>
    /// 图片修改功能组
    /// </summary>
    class 图片特效
    {
        /// <summary>
        /// 图片反色
        /// </summary>
        /// <param name="yuan">要反色的图片</param>
        /// <returns>底片后的结果</returns>
        public Bitmap 反色(Bitmap yuan)
        {
            try // 开始转换
            {
                Bitmap newbitmap = new Bitmap(yuan.Width, yuan.Height);
                Color pixel;
                for (int x = 1; x < yuan.Width; x++)
                {
                    for (int y = 1; y < yuan.Height; y++)
                    {
                        int r, g, b;
                        pixel = yuan.GetPixel(x, y);
                        r = 255 - pixel.R;
                        g = 255 - pixel.G;
                        b = 255 - pixel.B;
                        newbitmap.SetPixel(x, y, Color.FromArgb(r, g, b));
                    }
                }
                return newbitmap;
            }
            catch // 如果转换有错误
            {
                return yuan; // 返回原图 
            }
        }
        /// <summary>
        /// 图片浮雕化
        /// </summary>
        /// <param name="yuan">要修改的图片</param>
        /// <returns>修改后的结果</returns>
        public Bitmap 浮雕(Bitmap yuan)
        {
            try // 开始转换
            {
                Bitmap newBitmap = new Bitmap(yuan.Width, yuan.Height);
                Bitmap oldBitmap = yuan;
                Color pixel1, pixel2;
                for (int x = 0; x < yuan.Width - 1; x++)
                {
                    for (int y = 0; y < yuan.Height - 1; y++)
                    {
                        int r = 0, g = 0, b = 0;
                        pixel1 = oldBitmap.GetPixel(x, y);
                        pixel2 = oldBitmap.GetPixel(x + 1, y + 1);
                        r = Math.Abs(pixel1.R - pixel2.R + 128);
                        g = Math.Abs(pixel1.G - pixel2.G + 128);
                        b = Math.Abs(pixel1.B - pixel2.B + 128);
                        if (r > 255)
                        {
                            r = 255;
                        }
                        if (r < 0)
                        {
                            r = 0;
                        }
                        if (g > 255)
                        {
                            g = 255;
                        }
                        if (g < 0)
                        {
                            g = 0;
                        }
                        if (b > 255)
                        {
                            b = 255;
                        }
                        if (b < 0)
                        {
                            b = 0;
                        }
                        newBitmap.SetPixel(x, y, Color.FromArgb(r, g, b));
                    }
                }
                return newBitmap;
            }
            catch // 如果转换有错误
            {
                return yuan; // 返回原图
            }
        }
        /// <summary>
        /// 图片黑白化
        /// </summary>
        /// <param name="yuan">要修改的图片</param>
        /// <returns>修改后的图片</returns>
        public Bitmap 黑白(Bitmap yuan)
        {
            try // 开始转换
            {
                Bitmap newBitmap = new Bitmap(yuan.Width, yuan.Height);
                Bitmap oldBitmap = yuan;
                Color pixel;
                for (int x = 0; x < yuan.Width; x++)
                {
                    for (int y = 0; y < yuan.Height; y++)
                    {
                        pixel = oldBitmap.GetPixel(x, y);
                        int r, g, b, Result = 0;
                        r = pixel.R;
                        g = pixel.G;
                        b = pixel.B;
                        int iType = 2;
                        switch (iType)
                        {
                            case 0:
                                Result = ((r + g + b) / 3);
                                break;
                            case 1:
                                Result = r > g ? r : g;
                                Result = Result > b ? Result : b;
                                break;
                            case 2:
                                Result = ((int)(0.7 * r) + (int)(0.2 * g) + (int)(0.1 * b));
                                break;
                        }
                        newBitmap.SetPixel(x, y, Color.FromArgb(Result, Result, Result));
                    }
                }
                return newBitmap;
            }
            catch // 如果转换有错误
            {
                return yuan; // 返回原图
            }
        }
        /// <summary>
        /// 图片柔滑化
        /// </summary>
        /// <param name="yuan">要修改的照片</param>
        /// <returns>修改后的图片</returns>
        public Bitmap 柔滑(Bitmap yuan)
        {
            try // 开始转换
            {
                Bitmap bitmap = new Bitmap(yuan.Width, yuan.Height);
                Bitmap MyBitmap = yuan;
                Color pixel;
                int[] Gauss = { 1, 2, 1, 2, 4, 2, 1, 2, 1 };
                for (int x = 1; x < yuan.Width - 1; x++)
                {
                    for (int y = 1; y < yuan.Height - 1; y++)
                    {
                        int r = 0, g = 0, b = 0;
                        int Index = 0;
                        for (int col = -1; col <= 1; col++)
                        {
                            for (int row = -1; row <= 1; row++)
                            {
                                pixel = MyBitmap.GetPixel(x + row, y + col);
                                r += pixel.R * Gauss[Index];
                                g += pixel.G * Gauss[Index];
                                b += pixel.B * Gauss[Index];
                                Index++;
                            }
                        }
                        r /= 16;
                        g /= 16;
                        b /= 16;
                        r = r > 255 ? 255 : r;
                        r = r < 0 ? 0 : r;
                        g = g > 255 ? 255 : g;
                        g = g < 0 ? 0 : g;
                        b = b > 255 ? 255 : b;
                        b = b < 0 ? 0 : b;
                        bitmap.SetPixel(x - 1, y - 1, Color.FromArgb(r, g, b));
                    }
                }
                return bitmap;
            }
            catch // 如果转换有错误
            {
                return yuan; // 返回原图
            }
        }
        /// <summary>
        /// 图片锐化
        /// </summary>
        /// <param name="yuan">要修改的图片</param>
        /// <returns>修改后的图片</returns>
        public Bitmap 锐化(Bitmap yuan)
        {
            try // 开始转换
            {
                Bitmap newBitmap = new Bitmap(yuan.Width, yuan.Height);
                Bitmap oldBitmap = yuan;
                Color pixel;
                int[] Laplacian = { -1, -1, -1, -1, 9, -1, -1, -1, -1 };
                for (int x = 1; x < yuan.Width - 1; x++)
                {
                    for (int y = 1; y < yuan.Height - 1; y++)
                    {
                        int r = 0, g = 0, b = 0;
                        int Index = 0;
                        for (int col = -1; col <= 1; col++)
                        {
                            for (int rom = -1; rom <= 1; rom++)
                            {
                                pixel = oldBitmap.GetPixel(x + rom, y + col);
                                r += pixel.R * Laplacian[Index];
                                g += pixel.G * Laplacian[Index];
                                b += pixel.B * Laplacian[Index];
                                Index++;
                            }
                        }
                        r = r > 255 ? 255 : r;
                        r = r < 0 ? 0 : r;
                        g = g > 255 ? 255 : g;
                        g = g < 0 ? 0 : g;
                        b = b > 255 ? 255 : b;
                        b = b < 0 ? 0 : b;
                        newBitmap.SetPixel(x - 1, y - 1, Color.FromArgb(r, g, b));
                    }
                }
                return newBitmap;
            }
            catch // 如果转换有错误
            {
                return yuan; // 返回原图
            }
        }
        /// <summary>
        /// 图片油画化
        /// </summary>
        /// <param name="yuan">要修改的图片</param>
        /// <returns>修改后的图片</returns>
        public Bitmap 油画(Bitmap yuan)
        {
            try // 开始转换
            {
                Bitmap newBitmap = new Bitmap(yuan.Width, yuan.Height);
                Bitmap oldBitmap = yuan;
                Color pixel;
                Random rnd = new Random();
                for (int x = yuan.Width; x > 1; x--)
                {
                    for (int y = yuan.Height; y > 1; y--)
                    {
                        int iModel = 5;
                        int i = x - iModel;
                        if (i > 1)
                        {
                            int j = y - iModel;
                            if (j > 1)
                            {
                                int iPos = rnd.Next(100000) % iModel;
                                pixel = oldBitmap.GetPixel(i + iPos, j + iPos);
                                newBitmap.SetPixel(i, j, pixel);
                            }
                        }
                    }
                }
                return newBitmap;
            }
            catch // 如果有错误
            {
                return yuan; // 返回原图
            }
        }
        /// <summary>
        /// 图片马赛克
        /// </summary>
        /// <param name="bitmap">要马赛克的图片</param>
        /// <param name="effectWidth">马赛克程度</param>
        /// <returns>马赛克后的图片</returns>
        public System.Drawing.Bitmap 马赛克(System.Drawing.Bitmap bitmap, int effectWidth = 10)
        {
            // 差异最多的就是以照一定范围取样 完之后直接去下一个范围
            for (int heightOfffset = 0; heightOfffset < bitmap.Height; heightOfffset += effectWidth)
            {
                for (int widthOffset = 0; widthOffset < bitmap.Width; widthOffset += effectWidth)
                {
                    int avgR = 0, avgG = 0, avgB = 0;
                    int blurPixelCount = 0;
                    for (int x = widthOffset; (x < widthOffset + effectWidth && x < bitmap.Width); x++)
                    {
                        for (int y = heightOfffset; (y < heightOfffset + effectWidth && y < bitmap.Height); y++)
                        {
                            System.Drawing.Color pixel = bitmap.GetPixel(x, y);
                            avgR += pixel.R;
                            avgG += pixel.G;
                            avgB += pixel.B;
                            blurPixelCount++;
                        }
                    }
                    // 计算范围平均
                    avgR = avgR / blurPixelCount;
                    avgG = avgG / blurPixelCount;
                    avgB = avgB / blurPixelCount;
                    // 所有范围内都设定此值
                    for (int x = widthOffset; (x < widthOffset + effectWidth && x < bitmap.Width); x++)
                    {
                        for (int y = heightOfffset; (y < heightOfffset + effectWidth && y < bitmap.Height); y++)
                        {
                            System.Drawing.Color newColor = System.Drawing.Color.FromArgb(avgR, avgG, avgB);
                            bitmap.SetPixel(x, y, newColor);
                        }
                    }
                }
            }
            return bitmap;
        }
    }
    class 旋转
    {
        /// <summary>
        /// 图片旋转180°
        /// </summary>
        /// <param name="yuan">要旋转的图片</param>
        /// <returns>旋转后的图片</returns>
        public Bitmap 旋转180度(Bitmap yuan)
        {
            try
            {
                yuan.RotateFlip(RotateFlipType.Rotate180FlipNone);
            }
            catch { } // 忽略错误
            return yuan; // 返回结果
        }
        /// <summary>
        /// 图片顺时针旋转90°
        /// </summary>
        /// <param name="yuan">要旋转的图片</param>
        /// <returns>旋转后的图片</returns>
        public Bitmap 顺时针旋转90度(Bitmap yuan)
        {
            try
            {
                yuan.RotateFlip(RotateFlipType.Rotate270FlipXY);
            }
            catch { } // 忽略错误
            return yuan; // 返回结果
        }
        /// <summary>
        /// 图片逆时针旋转90°
        /// </summary>
        /// <param name="yuan">要旋转的图片</param>
        /// <returns>旋转后的图片</returns>
        public Bitmap 逆时针旋转90度(Bitmap yuan)
        {
            try
            {
                yuan.RotateFlip(RotateFlipType.Rotate90FlipXY);
            }
            catch { } // 忽略错误
            return yuan; // 返回结果
        }
        /// <summary>
        /// 图片垂直旋转
        /// </summary>
        /// <param name="yuan">要旋转的图片</param>
        /// <returns>旋转后的图片</returns>
        public Bitmap 垂直旋转(Bitmap yuan)
        {
            try
            {
                yuan.RotateFlip(RotateFlipType.Rotate180FlipX);
            }
            catch { } // 忽略错误
            return yuan; // 返回结果
        }
        /// <summary>
        /// 图片水平旋转
        /// </summary>
        /// <param name="yuan">要旋转的图片</param>
        /// <returns>旋转后的图片</returns>
        public Bitmap 水平旋转(Bitmap yuan)
        {
            try
            {
                yuan.RotateFlip(RotateFlipType.Rotate180FlipY);
            }
            catch { } // 忽略错误
            return yuan; // 返回结果
        }
        /// <summary>
        /// 将图片旋转N°（顺时针方向）
        /// </summary>
        /// <param name="b">要旋转的照片</param>
        /// <param name="angle">要旋转的度数</param>
        /// <returns></returns>
        public Bitmap 旋转任意度数(Bitmap b, int angle)
        {
            angle = angle % 360;
            //弧度转换 
            double radian = angle * Math.PI / 180.0;
            double cos = Math.Cos(radian);
            double sin = Math.Sin(radian);
            //原图的宽和高 
            int w = b.Width;
            int h = b.Height;
            int W = (int)(Math.Max(Math.Abs(w * cos - h * sin), Math.Abs(w * cos + h * sin)));
            int H = (int)(Math.Max(Math.Abs(w * sin - h * cos), Math.Abs(w * sin + h * cos)));
            //目标位图 
            Bitmap dsImage = new Bitmap(W, H);
            System.Drawing.Graphics g = System.Drawing.Graphics.FromImage(dsImage);
            g.InterpolationMode = System.Drawing.Drawing2D.InterpolationMode.Bilinear;
            g.SmoothingMode = System.Drawing.Drawing2D.SmoothingMode.HighQuality;
            //计算偏移量 
            Point Offset = new Point((W - w) / 2, (H - h) / 2);
            //构造图像显示区域:让图像的中心与窗口的中心点一致 
            Rectangle rect = new Rectangle(Offset.X, Offset.Y, w, h);
            Point center = new Point(rect.X + rect.Width / 2, rect.Y + rect.Height / 2);
            g.TranslateTransform(center.X, center.Y);
            g.RotateTransform(angle);
            //恢复图像在水平和垂直方向的平移 
            g.TranslateTransform(-center.X, -center.Y);
            g.DrawImage(b, rect);
            //重至绘图的所有变换 
            g.ResetTransform();
            g.Save();
            g.Dispose();
            return dsImage;
        }
    }
    /// <summary>
    /// 用于获取图片信息的类
    /// </summary>
    class 图片信息
    {
        /// <summary>
        /// 获取图片拍摄日期
        /// </summary>
        /// <param name="file">图片所在路径</param>
        /// <returns>返回日期（为字符串形式，如果没有日期，就返回空）</returns>
        public string 拍摄时间(string file)
        {
            Encoding ascii = Encoding.ASCII;
            string picDate;
            FileStream stream = new FileStream(file, FileMode.Open, FileAccess.Read);
            Image image = Image.FromStream(stream, true, false);
            foreach (PropertyItem p in image.PropertyItems)
            {
                //获取拍摄日期时间
                if (p.Id == 0x9003) // 0x0132 最后更新时间
                {
                    stream.Close();
                    picDate = ascii.GetString(p.Value);
                    if ((!"".Equals(picDate)) && picDate.Length >= 10)
                    {
                        // 拍摄日期
                        picDate = picDate.Substring(0, 10);
                        picDate = picDate.Replace(":", "-");
                        return picDate;
                    }
                }
            }
            stream.Close();
            return "";
        }
    }
}

```
至于如何调用这个命名空间，相信不用多说，**不会就上Baidu**。
# 程序示例代码（例子）
如下

```csharp
/*
 ********************************************************************
 *程序信息：                                                        *
 *    更新时间（最近一次）：2020年7月30日08:53:34                   *
 *    作者：gfdgd xi                                                *
 *    调试平台：Visual Studio 2017 企业版 以及 Windows 8.1          *
 *    程序目的：以最简单的方式修改图片                              *
 *    难道：★★★☆☆                                              *
 *    源码：公开                                                    *
 *    版本：1.1（代码更加整洁，没1.0那么混乱，代码注释更多）        *
 ********************************************************************
 */
// using System.Collections.Generic;
// using System.ComponentModel;
// using System.Data;
// using System.Linq;
// using System.Linq.Expressions;
// 这些头文件不重要，所以被注释了
using System.Text;
using System.Drawing;
using System.Drawing.Imaging;
using System;
using System.Windows.Forms;
using System.IO;
using 修改图片; // 自己图片的类


namespace 图片修改
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
            // 添加图片显示方式下拉框的内容
            string[] values = Enum.GetNames(typeof(PictureBoxSizeMode));
            toolStripComboBox1.Items.AddRange(values);
            toolStripComboBox1.SelectedIndex = 4;
            PictureBoxSizeMode si = (PictureBoxSizeMode)Enum.Parse(typeof(PictureBoxSizeMode), "Zoom");
            pictureBox1.SizeMode = si;
        }
        Bitmap chehui, huanyuan, firstpicture; // 定义3个变量，分别储存上一步操作的图片，撤回前的图片，最先的图片
        string openpath;
        private void 重置图片ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            if (MessageBox.Show("你确定要撤回到最初始的图片吗？",
                "提示",
                MessageBoxButtons.YesNo,
                MessageBoxIcon.Question)
                == DialogResult.Yes) // 询问用户是否要撤回
            {
                // 如果用户要
                chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
                /* 设置控件 */
                撤回ToolStripMenuItem.Enabled = true;
                还原ToolStripMenuItem.Enabled = false;
                pictureBox1.Image = firstpicture; // 把图片控件里的图片替换成原图片
                this.Text = "*" + openpath; // 设置窗口标题
            }
        }

        private void toolStripComboBox1_SelectedIndexChanged(object sender, EventArgs e) // 设置图片显示方式
        {
            string val = toolStripComboBox1.SelectedItem as string;
            pictureBox1.SizeMode = (PictureBoxSizeMode)Enum.Parse(typeof(PictureBoxSizeMode), val);
        }
        图片特效 changepicture = new 图片特效(); // 调用图片修改的类
        private void 底片ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            pictureBox1.Image = changepicture.反色((Bitmap)pictureBox1.Image); // 调用反色的方法
        }

        private void 黑白ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            pictureBox1.Image = changepicture.黑白((Bitmap)pictureBox1.Image); // 调用黑白的方法
        }

        private void 柔滑ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            pictureBox1.Image = changepicture.柔滑((Bitmap)pictureBox1.Image); // 调用柔滑的方法
        }

        private void 锐化ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            pictureBox1.Image = changepicture.锐化((Bitmap)pictureBox1.Image); // 调用锐化的方法
        }

        private void 油画ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            pictureBox1.Image = changepicture.油画((Bitmap)pictureBox1.Image); // 调用油画的方法
        }

        private void 撤回ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            // 撤回图片
            huanyuan = (Bitmap)pictureBox1.Image; // 保存还原信息，防止用户误撤回
            /* 设置控件 */
            还原ToolStripMenuItem.Enabled = true;
            撤回ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            pictureBox1.Image = chehui; // 撤回操作
        }

        private void 还原ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            // 还原图片
            chehui = (Bitmap)pictureBox1.Image; // 保存还原信息，防止用户误撤回
            /* 设置控件 */
            还原ToolStripMenuItem.Enabled = false;
            撤回ToolStripMenuItem.Enabled = true;
            this.Text = "*" + openpath; // 设置窗口标题
            pictureBox1.Image = huanyuan; // 还原操作
        }

        private void 另存为SToolStripMenuItem_Click(object sender, EventArgs e)
        {
            if(saveFileDialog1.ShowDialog()
                == DialogResult.OK) // 如果用户确定保存的操作
            {
                try
                {
                    switch (saveFileDialog1.FilterIndex) // 根据用户在另存为对话框里选择的文件类型进行不同的保存
                    {
                        case 1: // 选择了PNG选项
                            pictureBox1.Image.Save(saveFileDialog1.FileName, ImageFormat.Png);
                            break;
                        case 2: // 选择了JPG选项
                            pictureBox1.Image.Save(saveFileDialog1.FileName, ImageFormat.Jpeg);
                            break;
                        case 3: // 选择了GIF选项
                            pictureBox1.Image.Save(saveFileDialog1.FileName, ImageFormat.Gif);
                            break;
                        case 4: // 选择了BMP选项
                            pictureBox1.Image.Save(saveFileDialog1.FileName, ImageFormat.Bmp);
                            break;
                        case 5: // 选择了全部文件选项
                            pictureBox1.Image.Save(saveFileDialog1.FileName);
                            break;
                    }
                    openpath = saveFileDialog1.FileName;
                    this.Text = openpath; // 设置窗口标题
                }
                catch(Exception ex) // 如果保存过程有错
                {
                    MessageBox.Show(ex.Message, "错误", MessageBoxButtons.OK, MessageBoxIcon.Error); // 就抛出错误
                }
            }
        }

        private void 保存SToolStripMenuItem_Click(object sender, EventArgs e)
        {
            try
            {
                pictureBox1.Image.Save(openpath, ImageFormat.Png);
                this.Text = openpath; // 设置窗口标题
            }
            catch(Exception ex)
            {
                MessageBox.Show(ex.Message, "错误", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
        }

        private void 浮雕ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            pictureBox1.Image = changepicture.浮雕((Bitmap)pictureBox1.Image); // 调用浮雕的方法
        }

        private void Form1_FormClosing(object sender, FormClosingEventArgs e)
        {
            e.Cancel = true; // 不然程序这么快退出
            if(MessageBox.Show("你确定要退出程序吗？",
                "提示",
                MessageBoxButtons.YesNo,
                MessageBoxIcon.Question) == 
                DialogResult.Yes) // 如果用户选择了是
            {
                switch(this.Text.StartsWith("*")) // 获取程序标题开头有没有*符号
                {
                    case true: // 如果有
                        if (MessageBox.Show("你修改的图片还没有保存呢！\n你确定要退出吗？",
                            "警告",
                            MessageBoxButtons.YesNo,
                            MessageBoxIcon.Warning) ==
                            DialogResult.Yes) // 如果用户选择了是
                        {
                            e.Cancel = false;
                        }
                            break;
                    case false: // 如果没有
                        e.Cancel = false; // 程序退出
                        break;
                }
            }
        }

        private void 退出EToolStripMenuItem_Click(object sender, EventArgs e)
        {
            this.Close(); // 触发程序关闭事件
        }
        旋转 Get = new 旋转();
        private void 旋转180ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            pictureBox1.Image = Get.旋转180度((Bitmap)pictureBox1.Image); // 旋转180°
        }

        private void 顺时针旋转90ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            pictureBox1.Image = Get.顺时针旋转90度((Bitmap)pictureBox1.Image); // 顺时针旋转90°
        }

        private void 逆时针旋转90ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            pictureBox1.Image = Get.逆时针旋转90度((Bitmap)pictureBox1.Image); // 逆时针旋转90°
        }

        private void 水平旋转ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            pictureBox1.Image = Get.水平旋转((Bitmap)pictureBox1.Image); // 水平旋转
        }

        private void 垂直旋转ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            pictureBox1.Image = Get.垂直旋转((Bitmap)pictureBox1.Image); // 垂直旋转
        }

        private void 打开其他主题OToolStripMenuItem_Click(object sender, EventArgs e)
        {
            if(openFileDialog2.ShowDialog() == 
                DialogResult.OK) // 如果用户选择了主题文件并点击了“确定”
            {
                skinEngine1.SkinFile = openFileDialog2.FileName; // 打开主题文件
                默认主题ToolStripMenuItem.Text = openFileDialog2.FileName;
            }
        }
        private void 图片马赛克ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            try
            {
                pictureBox1.Image = changepicture.马赛克((Bitmap)pictureBox1.Image, Convert.ToInt32(toolStripTextBox1.Text));
            }
            catch(Exception ex) // 如果出现错误
            {
                MessageBox.Show(ex.Message, "错误", MessageBoxButtons.OK, MessageBoxIcon.Error); // 抛出错误
            }
            
        }
        private void 旋转图片ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            try
            {
                pictureBox1.Image = Get.旋转任意度数((Bitmap)pictureBox1.Image, Convert.ToInt32(toolStripTextBox2.Text)); // 旋转用户指定的度数
            }
            catch (Exception ex) // 如果出现错误
            {
                MessageBox.Show(ex.Message, "错误", MessageBoxButtons.OK, MessageBoxIcon.Error); // 抛出错误
            }   
        }

        private void 要替换的颜色点此设置ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            if(colorDialog1.ShowDialog() ==
                DialogResult.OK) // 如果用户选择了颜色
            {
                toolStripMenuItem2.Text = colorDialog1.Color.Name; // 将获取的颜色名称显示出来
            }
        }
        颜色 colour = new 颜色();
        private void 替换ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            try
            {
                pictureBox1.Image = colour.将指定颜色替换为透明((Bitmap)pictureBox1.Image, colorDialog1.Color); // 替换为透明颜色
            }
            catch (Exception ex) // 如果出现错误
            {
                MessageBox.Show(ex.Message, "错误", MessageBoxButtons.OK, MessageBoxIcon.Error); // 抛出错误
            }
        }

        private void 替换ToolStripMenuItem1_Click(object sender, EventArgs e)
        {
            chehui = (Bitmap)pictureBox1.Image; // 将现在显示的内容存入撤回变量里，到时候错误操作可以撤回
            /* 设置控件 */
            撤回ToolStripMenuItem.Enabled = true;
            还原ToolStripMenuItem.Enabled = false;
            this.Text = "*" + openpath; // 设置窗口标题
            /* End */
            try
            {
                pictureBox1.Image = colour.替换颜色((Bitmap)pictureBox1.Image, 要替换的颜色.Color, 替换后的颜色.Color); // 替换颜色
            }
            catch (Exception ex) // 如果出现错误
            {
                MessageBox.Show(ex.Message, "错误", MessageBoxButtons.OK, MessageBoxIcon.Error); // 抛出错误
            }
        }

        private void 点此设置ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            if(要替换的颜色.ShowDialog() 
                == DialogResult.OK) // 如果用户选择了颜色
            {
                toolStripMenuItem3.Text = 要替换的颜色.Color.Name; // 将选择的颜色显示在控件上
            }
        }

        private void 设置ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            if (替换后的颜色.ShowDialog()
                == DialogResult.OK) // 如果用户选择了颜色
            {
                toolStripMenuItem4.Text = 替换后的颜色.Color.Name; // 将选择的颜色显示在控件上
            }
        }

        private void 查看ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            图片信息 picture = new 图片信息(); // 调用实例
            Bitmap bitmap = new Bitmap("Temp\\" + tempthingname.ToString()); // 打开图片
            try
            {
                MessageBox.Show("图片存放位置：：" + openFileDialog1.FileName + // 显示对话框提示信息
                              "\n图片大小：" + bitmap.Width + "×" + bitmap.Height +
                              "\n图片格式：" + bitmap.RawFormat
                              + "\n拍摄时间：" + picture.拍摄时间("Temp\\" + tempthingname.ToString()),
                              "图片信息"); // 设置图片标题
            }
            catch(Exception ex)
            {
                MessageBox.Show(ex.Message, "错误", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
        }

        int tempthingname = 0; // 创建一个变量，储存临时目录文件名
        private void 打开OToolStripMenuItem_Click(object sender, EventArgs e)
        {
            tempthingname++; // 数字要+1，不然照样提示资源占用
            if (openFileDialog1.ShowDialog()
                == DialogResult.OK) // 如果用户选择了文件并点击了确定
            {
                try
                {
                    if (File.Exists("Temp\\" + tempthingname.ToString())) File.Delete("Temp\\" + tempthingname.ToString()); // 如果文件存在，就删了它
                    File.Copy(openFileDialog1.FileName, "Temp\\"+tempthingname.ToString()); // 将图片拷贝到临时目录，不在保存时提示资源占用
                    pictureBox1.Image = new Bitmap("Temp\\" + tempthingname.ToString()); // 打开图片文件
                    /* ——设置控件—— */
                    保存SToolStripMenuItem.Enabled = true;
                    另存为SToolStripMenuItem.Enabled = true;
                    操作ToolStripMenuItem.Enabled = true;
                    图片ToolStripMenuItem.Enabled = true;
                    this.Text = openFileDialog1.FileName; // 设置窗口标题
                    撤回ToolStripMenuItem.Enabled = false; // 图片还没修改呢，就可以撤回了？
                    还原ToolStripMenuItem.Enabled = false;
                    /* 将打开的图片保存到最先图片的变量里 */
                    firstpicture = new Bitmap("Temp\\" + tempthingname.ToString());
                    /* 将打开的图片路径保存到变量里 */
                    openpath = openFileDialog1.FileName;
                    
                }
                catch (Exception ex) // 如果上述语句在运行时出错
                {
                    MessageBox.Show(ex.Message, "错误", MessageBoxButtons.OK, MessageBoxIcon.Error); // 抛出错误
                    /* ——设置控件，和上述语句运行时无错的控件设置相反—— */
                    保存SToolStripMenuItem.Enabled = false;
                    另存为SToolStripMenuItem.Enabled = false;
                    操作ToolStripMenuItem.Enabled = false;
                    图片ToolStripMenuItem.Enabled = false;
                }
            }
        }
    }
}
/* ——————————————————分界线———————————————————————— */
// 修改图片的命名空间
// 核心代码！
/// <summary>
/// 图片修改
/// </summary>
namespace 修改图片
{
    /// <summary>
    /// 图片颜色基本操作
    /// </summary>
    class 颜色
    {
        /// <summary>
        /// 将图片指定的颜色替换为透明颜色
        /// </summary>
        /// <param name="yuan">原来的图片</param>
        /// <param name="ti">要替换的颜色</param>
        /// <returns>替换后的结果</returns>
        public Bitmap 将指定颜色替换为透明(Bitmap yuan, Color ti)
        {
            yuan.MakeTransparent(ti);
            return yuan;
        }
        /// <summary>
        /// 将A颜色替换为B颜色
        /// </summary>
        /// <param name="yuan">要修改的图片</param>
        /// <param name="a">要替换的颜色</param>
        /// <param name="b">要替换成的颜色</param>
        /// <returns>替换后结果的图片</returns>
        public Bitmap 替换颜色(Bitmap yuan,Color a,Color b)
        {
            for(int x=1;x<yuan.Width;x++) // 将每个x轴都循环一遍
            {
                for(int y=1;y<yuan.Height;y++) // 将每个y轴循环一遍
                {
                    if(yuan.GetPixel(x,y).ToArgb() == a.ToArgb()) // 将颜色转为32位Argb结构，如果值相等，就
                    {
                        yuan.SetPixel(x, y, b); // 将指定x轴和y轴设定为指定颜色
                    }
                }
            }
            return yuan;
        }
    }
    /// <summary>
    /// 图片修改功能组
    /// </summary>
    class 图片特效
    {
        /// <summary>
        /// 图片反色
        /// </summary>
        /// <param name="yuan">要反色的图片</param>
        /// <returns>底片后的结果</returns>
        public Bitmap 反色(Bitmap yuan)
        {
            try // 开始转换
            {
                Bitmap newbitmap = new Bitmap(yuan.Width, yuan.Height);
                Color pixel;
                for (int x = 1; x < yuan.Width; x++)
                {
                    for (int y = 1; y < yuan.Height; y++)
                    {
                        int r, g, b;
                        pixel = yuan.GetPixel(x, y);
                        r = 255 - pixel.R;
                        g = 255 - pixel.G;
                        b = 255 - pixel.B;
                        newbitmap.SetPixel(x, y, Color.FromArgb(r, g, b));
                    }
                }
                return newbitmap;
            }
            catch // 如果转换有错误
            {
                return yuan; // 返回原图 
            }
        }
        /// <summary>
        /// 图片浮雕化
        /// </summary>
        /// <param name="yuan">要修改的图片</param>
        /// <returns>修改后的结果</returns>
        public Bitmap 浮雕(Bitmap yuan)
        {
            try // 开始转换
            {
                Bitmap newBitmap = new Bitmap(yuan.Width, yuan.Height);
                Bitmap oldBitmap = yuan;
                Color pixel1, pixel2;
                for (int x = 0; x < yuan.Width - 1; x++)
                {
                    for (int y = 0; y < yuan.Height - 1; y++)
                    {
                        int r = 0, g = 0, b = 0;
                        pixel1 = oldBitmap.GetPixel(x, y);
                        pixel2 = oldBitmap.GetPixel(x + 1, y + 1);
                        r = Math.Abs(pixel1.R - pixel2.R + 128);
                        g = Math.Abs(pixel1.G - pixel2.G + 128);
                        b = Math.Abs(pixel1.B - pixel2.B + 128);
                        if (r > 255)
                        {
                            r = 255;
                        }
                        if (r < 0)
                        {
                            r = 0;
                        }
                        if (g > 255)
                        {
                            g = 255;
                        }
                        if (g < 0)
                        {
                            g = 0;
                        }
                        if (b > 255)
                        {
                            b = 255;
                        }
                        if (b < 0)
                        {
                            b = 0;
                        }
                        newBitmap.SetPixel(x, y, Color.FromArgb(r, g, b));
                    }
                }
                return newBitmap;
            }
            catch // 如果转换有错误
            {
                return yuan; // 返回原图
            }
        }
        /// <summary>
        /// 图片黑白化
        /// </summary>
        /// <param name="yuan">要修改的图片</param>
        /// <returns>修改后的图片</returns>
        public Bitmap 黑白(Bitmap yuan)
        {
            try // 开始转换
            {
                Bitmap newBitmap = new Bitmap(yuan.Width, yuan.Height);
                Bitmap oldBitmap = yuan;
                Color pixel;
                for (int x = 0; x < yuan.Width; x++)
                {
                    for (int y = 0; y < yuan.Height; y++)
                    {
                        pixel = oldBitmap.GetPixel(x, y);
                        int r, g, b, Result = 0;
                        r = pixel.R;
                        g = pixel.G;
                        b = pixel.B;
                        int iType = 2;
                        switch (iType)
                        {
                            case 0:
                                Result = ((r + g + b) / 3);
                                break;
                            case 1:
                                Result = r > g ? r : g;
                                Result = Result > b ? Result : b;
                                break;
                            case 2:
                                Result = ((int)(0.7 * r) + (int)(0.2 * g) + (int)(0.1 * b));
                                break;
                        }
                        newBitmap.SetPixel(x, y, Color.FromArgb(Result, Result, Result));
                    }
                }
                return newBitmap;
            }
            catch // 如果转换有错误
            {
                return yuan; // 返回原图
            }
        }
        /// <summary>
        /// 图片柔滑化
        /// </summary>
        /// <param name="yuan">要修改的照片</param>
        /// <returns>修改后的图片</returns>
        public Bitmap 柔滑(Bitmap yuan)
        {
            try // 开始转换
            {
                Bitmap bitmap = new Bitmap(yuan.Width, yuan.Height);
                Bitmap MyBitmap = yuan;
                Color pixel;
                int[] Gauss = { 1, 2, 1, 2, 4, 2, 1, 2, 1 };
                for (int x = 1; x < yuan.Width - 1; x++)
                {
                    for (int y = 1; y < yuan.Height - 1; y++)
                    {
                        int r = 0, g = 0, b = 0;
                        int Index = 0;
                        for (int col = -1; col <= 1; col++)
                        {
                            for (int row = -1; row <= 1; row++)
                            {
                                pixel = MyBitmap.GetPixel(x + row, y + col);
                                r += pixel.R * Gauss[Index];
                                g += pixel.G * Gauss[Index];
                                b += pixel.B * Gauss[Index];
                                Index++;
                            }
                        }
                        r /= 16;
                        g /= 16;
                        b /= 16;
                        r = r > 255 ? 255 : r;
                        r = r < 0 ? 0 : r;
                        g = g > 255 ? 255 : g;
                        g = g < 0 ? 0 : g;
                        b = b > 255 ? 255 : b;
                        b = b < 0 ? 0 : b;
                        bitmap.SetPixel(x - 1, y - 1, Color.FromArgb(r, g, b));
                    }
                }
                return bitmap;
            }
            catch // 如果转换有错误
            {
                return yuan; // 返回原图
            }
        }
        /// <summary>
        /// 图片锐化
        /// </summary>
        /// <param name="yuan">要修改的图片</param>
        /// <returns>修改后的图片</returns>
        public Bitmap 锐化(Bitmap yuan)
        {
            try // 开始转换
            {
                Bitmap newBitmap = new Bitmap(yuan.Width, yuan.Height);
                Bitmap oldBitmap = yuan;
                Color pixel;
                int[] Laplacian = { -1, -1, -1, -1, 9, -1, -1, -1, -1 };
                for (int x = 1; x < yuan.Width - 1; x++)
                {
                    for (int y = 1; y < yuan.Height - 1; y++)
                    {
                        int r = 0, g = 0, b = 0;
                        int Index = 0;
                        for (int col = -1; col <= 1; col++)
                        {
                            for (int rom = -1; rom <= 1; rom++)
                            {
                                pixel = oldBitmap.GetPixel(x + rom, y + col);
                                r += pixel.R * Laplacian[Index];
                                g += pixel.G * Laplacian[Index];
                                b += pixel.B * Laplacian[Index];
                                Index++;
                            }
                        }
                        r = r > 255 ? 255 : r;
                        r = r < 0 ? 0 : r;
                        g = g > 255 ? 255 : g;
                        g = g < 0 ? 0 : g;
                        b = b > 255 ? 255 : b;
                        b = b < 0 ? 0 : b;
                        newBitmap.SetPixel(x - 1, y - 1, Color.FromArgb(r, g, b));
                    }
                }
                return newBitmap;
            }
            catch // 如果转换有错误
            {
                return yuan; // 返回原图
            }
        }
        /// <summary>
        /// 图片油画化
        /// </summary>
        /// <param name="yuan">要修改的图片</param>
        /// <returns>修改后的图片</returns>
        public Bitmap 油画(Bitmap yuan)
        {
            try // 开始转换
            {
                Bitmap newBitmap = new Bitmap(yuan.Width, yuan.Height);
                Bitmap oldBitmap = yuan;
                Color pixel;
                Random rnd = new Random();
                for (int x = yuan.Width; x > 1; x--)
                {
                    for (int y = yuan.Height; y > 1; y--)
                    {
                        int iModel = 5;
                        int i = x - iModel;
                        if (i > 1)
                        {
                            int j = y - iModel;
                            if (j > 1)
                            {
                                int iPos = rnd.Next(100000) % iModel;
                                pixel = oldBitmap.GetPixel(i + iPos, j + iPos);
                                newBitmap.SetPixel(i, j, pixel);
                            }
                        }
                    }
                }
                return newBitmap;
            }
            catch // 如果有错误
            {
                return yuan; // 返回原图
            }
        }
        /// <summary>
        /// 图片马赛克
        /// </summary>
        /// <param name="bitmap">要马赛克的图片</param>
        /// <param name="effectWidth">马赛克程度</param>
        /// <returns>马赛克后的图片</returns>
        public System.Drawing.Bitmap 马赛克(System.Drawing.Bitmap bitmap, int effectWidth = 10)
        {
            // 差异最多的就是以照一定范围取样 完之后直接去下一个范围
            for (int heightOfffset = 0; heightOfffset < bitmap.Height; heightOfffset += effectWidth)
            {
                for (int widthOffset = 0; widthOffset < bitmap.Width; widthOffset += effectWidth)
                {
                    int avgR = 0, avgG = 0, avgB = 0;
                    int blurPixelCount = 0;
                    for (int x = widthOffset; (x < widthOffset + effectWidth && x < bitmap.Width); x++)
                    {
                        for (int y = heightOfffset; (y < heightOfffset + effectWidth && y < bitmap.Height); y++)
                        {
                            System.Drawing.Color pixel = bitmap.GetPixel(x, y);
                            avgR += pixel.R;
                            avgG += pixel.G;
                            avgB += pixel.B;
                            blurPixelCount++;
                        }
                    }
                    // 计算范围平均
                    avgR = avgR / blurPixelCount;
                    avgG = avgG / blurPixelCount;
                    avgB = avgB / blurPixelCount;
                    // 所有范围内都设定此值
                    for (int x = widthOffset; (x < widthOffset + effectWidth && x < bitmap.Width); x++)
                    {
                        for (int y = heightOfffset; (y < heightOfffset + effectWidth && y < bitmap.Height); y++)
                        {
                            System.Drawing.Color newColor = System.Drawing.Color.FromArgb(avgR, avgG, avgB);
                            bitmap.SetPixel(x, y, newColor);
                        }
                    }
                }
            }
            return bitmap;
        }
    }
    class 旋转
    {
        /// <summary>
        /// 图片旋转180°
        /// </summary>
        /// <param name="yuan">要旋转的图片</param>
        /// <returns>旋转后的图片</returns>
        public Bitmap 旋转180度(Bitmap yuan)
        {
            try
            {
                yuan.RotateFlip(RotateFlipType.Rotate180FlipNone);
            }
            catch { } // 忽略错误
                return yuan; // 返回结果
        }
        /// <summary>
        /// 图片顺时针旋转90°
        /// </summary>
        /// <param name="yuan">要旋转的图片</param>
        /// <returns>旋转后的图片</returns>
        public Bitmap 顺时针旋转90度(Bitmap yuan)
        {
            try
            {
                yuan.RotateFlip(RotateFlipType.Rotate270FlipXY);
            }
            catch { } // 忽略错误
            return yuan; // 返回结果
        }
        /// <summary>
        /// 图片逆时针旋转90°
        /// </summary>
        /// <param name="yuan">要旋转的图片</param>
        /// <returns>旋转后的图片</returns>
        public Bitmap 逆时针旋转90度(Bitmap yuan)
        {
            try
            {
                yuan.RotateFlip(RotateFlipType.Rotate90FlipXY);
            }
            catch{} // 忽略错误
            return yuan; // 返回结果
        }
        /// <summary>
        /// 图片垂直旋转
        /// </summary>
        /// <param name="yuan">要旋转的图片</param>
        /// <returns>旋转后的图片</returns>
        public Bitmap 垂直旋转(Bitmap yuan)
        {
            try
            {
                yuan.RotateFlip(RotateFlipType.Rotate180FlipX);
            }
            catch { } // 忽略错误
            return yuan; // 返回结果
        }
        /// <summary>
        /// 图片水平旋转
        /// </summary>
        /// <param name="yuan">要旋转的图片</param>
        /// <returns>旋转后的图片</returns>
        public Bitmap 水平旋转(Bitmap yuan)
        {
            try
            {
                yuan.RotateFlip(RotateFlipType.Rotate180FlipY);
            }
            catch { } // 忽略错误
            return yuan; // 返回结果
        }
        /// <summary>
        /// 将图片旋转N°（逆时针方向）
        /// </summary>
        /// <param name="b">要旋转的照片</param>
        /// <param name="angle">要旋转的度数</param>
        /// <returns></returns>
        public Bitmap 旋转任意度数(Bitmap b, int angle)
        {
            angle = angle % 360;
            //弧度转换 
            double radian = angle * Math.PI / 180.0;
            double cos = Math.Cos(radian);
            double sin = Math.Sin(radian);
            //原图的宽和高 
            int w = b.Width;
            int h = b.Height;
            int W = (int)(Math.Max(Math.Abs(w * cos - h * sin), Math.Abs(w * cos + h * sin)));
            int H = (int)(Math.Max(Math.Abs(w * sin - h * cos), Math.Abs(w * sin + h * cos)));
            //目标位图 
            Bitmap dsImage = new Bitmap(W, H);
            System.Drawing.Graphics g = System.Drawing.Graphics.FromImage(dsImage);
            g.InterpolationMode = System.Drawing.Drawing2D.InterpolationMode.Bilinear;
            g.SmoothingMode = System.Drawing.Drawing2D.SmoothingMode.HighQuality;
            //计算偏移量 
            Point Offset = new Point((W - w) / 2, (H - h) / 2);
            //构造图像显示区域:让图像的中心与窗口的中心点一致 
            Rectangle rect = new Rectangle(Offset.X, Offset.Y, w, h);
            Point center = new Point(rect.X + rect.Width / 2, rect.Y + rect.Height / 2);
            g.TranslateTransform(center.X, center.Y);
            g.RotateTransform(angle);
            //恢复图像在水平和垂直方向的平移 
            g.TranslateTransform(-center.X, -center.Y);
            g.DrawImage(b, rect);
            //重至绘图的所有变换 
            g.ResetTransform();
            g.Save();
            g.Dispose();
            return dsImage;
        }
    }
    /// <summary>
    /// 用于获取图片信息的类
    /// </summary>
    class 图片信息
    {
        /// <summary>
        /// 获取图片拍摄日期
        /// </summary>
        /// <param name="file">图片所在路径</param>
        /// <returns>返回日期（为字符串形式，如果没有日期，就返回空）</returns>
        public string 拍摄时间(string file)
        {
            Encoding ascii = Encoding.ASCII;
            string picDate;
            FileStream stream = new FileStream(file, FileMode.Open, FileAccess.Read);
            Image image = Image.FromStream(stream, true, false);
            foreach (PropertyItem p in image.PropertyItems)
            { 
                //获取拍摄日期时间
                if (p.Id == 0x9003) // 0x0132 最后更新时间
                {
                    stream.Close();
                    picDate = ascii.GetString(p.Value);
                    if ((!"".Equals(picDate)) && picDate.Length >= 10)
                    {
                        // 拍摄日期
                        picDate = picDate.Substring(0, 10);
                        picDate = picDate.Replace(":", "-");
                        return picDate;
                    }
                }
            }
            stream.Close();
            return "";
        }
    }
    }
```
（例子）示例程序执行效果图：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730085240559.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
不知道为什么点击查看图片信息时会提示

```csharp
Capacity exceeds maximum capacity.
Parameter name: capacity
```
百度翻译为

```csharp
容量超过最大容量。
参数名称：容量
```
暂时没搞清楚怎么回事

# 示例程序下载

示例程序下载地址：
[百度网盘下载地址，提取码：569u](https://pan.baidu.com/s/1Mo0Sr7nAiDfLePfluzGlZg)
[蓝奏云下载链接](https://gfdgdxi.lanzous.com/b01nmioih)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200725184729629.png)

# 程序修改的图片效果

——————下面是用这个程序修改的图片效果了，好奇效果的就接着往下看——————
原始照片：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200725172139782.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)


程序制作反色图片的结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200725171723156.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作浮雕图片的结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200725171844967.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作黑白图片的结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200725171922413.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作柔滑图片的结果（这张照片看起来没有大的变化）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200725172020350.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作锐化图片的结果（emm，这张照片锐化后有点……）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200725172336434.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作油画图片的结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200725172445777.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作图片旋转180°的结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/202007251725343.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作图片顺时针旋转90°的结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/202007251726310.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作图片逆时针旋转90°的结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200725172703267.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作图片水平旋转的结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200725172752370.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作图片垂直旋转的结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200725173119324.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作图片马赛克的结果（程度为10）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200725173254558.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作的透明图片效果（将白色设置为透明色，如果在这里看样子没区别，可以下载到本地上看一看）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730085820633.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
程序制作的颜色替换效果（将白色替换为黑色，替换后结果有点……）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730090016912.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

# 更新情况

一更（2020-07-25 18:28:11）：写下了这篇博客
二更：修改了代码部分，添加了一些功能（旋转任意度数、替换颜色【可以替换透明色】、获取图片拍摄信息）
**三更（2020年8月23日16:45:03）：发现程序bug，bug已经在注释标明，暂不知如何处理**

```csharp
/*
 *********************************************************************************************************************************
 * Bug 已知列表：                                                                                                                *
 *     1、修复在旋转图片操作时，原图也会被修改的情况，波及范围：旋转180度、逆时针旋转90度、顺时针旋转90度、垂直旋转、水平旋转    *
 *     （时间：2020-8-23 16:12:23）                                                                                              *
 *     解决方法：可先用“旋转任意度数”方法旋转图片，旋转可能有损或在以相反操作操作图片，恢复初始状态。                          *
 *     原因：未知。                                                                                                              *
 *     原代码（部分）：                                                                                                          *
 *     /// <summary>                                                                                                             *
 *      /// 图片顺时针旋转90°                                                                                                   *
 *      /// </summary>                                                                                                           *
 *      /// <param name="yuan">要旋转的图片</param>                                                                              *
 *      /// <returns>旋转后的图片</returns>                                                                                      *
 *      public Bitmap 顺时针旋转90度(Bitmap yuan)                                                                                *
 *      {                                                                                                                        *
 *          try                                                                                                                  *
 *          {                                                                                                                    *
 *              yuan.RotateFlip(RotateFlipType.Rotate270FlipXY);                                                                 *
 *          }                                                                                                                    *
 *          catch { } // 忽略错误                                                                                                *
 *          return yuan; // 返回结果                                                                                             *
 *      }                                                                                                                        *
 *********************************************************************************************************************************
 */
```

# End

（太多了，我自己都有点受不了）

