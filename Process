from tkinter import *
from tkinter.ttk import *
from tkinter import ttk

class QuanLyChiTieu:
    def __init__(self):
        self.Dic={}
        self.TongCTNgay=0
        self.TongCTThang=0
        self.TongTCNgay=0
        self.TongTCThang =0
        self.CTThang=[]
        for i in range(30):
            list=[]
            self.CTThang.append(list)
        # PHẦN GIAO DIỆN
        self.window= Tk()
        self.window.title("Quản lý chi tiêu")
        self.window.geometry("850x420")
        self.window.resizable(width=False,height=False)

        # Phần tiêu đề
        self.Tieude = Label(master=self.window,text="QUẢN LÝ CHI TIÊU",font=("#9Slide03 Nokia Regular",20,"bold"))
        self.Tieude.place(x=220,y=8)

        # Danh sách tháng
        self.Thang = Label(master=self.window,text="Tháng 5",font=("Arial",15,"bold"))
        # self.DSThang= Combobox(self.window,state="readonly")
        # self.DSThang['value']=("Tháng 1","Tháng 2","Tháng 3",
        #                 "Tháng 4","Tháng 5","Tháng 6",
        #                 "Tháng 7","Tháng 8","Tháng 9",
        #                 "Tháng 10","Tháng 11","Tháng 12")
        self.Thang.place(x= 120,y=75)
        # self.DSThang.place(x=120,y=82)

        # Danh sách ngày
        self.Ngay= Label(master=self.window,text="Ngày",font=("Arial",10,"bold"))
        self.DSNgay= Combobox(self.window,state="readonly")
        self.DSNgay['value']=("1","2","3","4","5","6","7","8","9","10",
                        "11","12","13","14","15","16","17","18","19","20",
                        "21","22","23","24","25","26","27","28","29","30")
        self.Ngay.place(x=40,y=110)
        self.DSNgay.place(x=120,y=112)
        self.DSNgay.bind("<<ComboboxSelected>>", self.Thong_tin_ngay)

        # Số dư
        self.Trocap = Label(master=self.window,text="Trợ cấp",font=("Arial",10,"bold"))
        self.TrocapEntry = Entry(master=self.window,width=23)
        self.Trocap.place(x=40,y=140)
        self.TrocapEntry.place(x=120,y=142)

        # Phần danh sách chi tiêu
        self.Chitieu= Label(master=self.window,text="Chi tiêu",font=("Arial",10,"bold"))
        self.DSChiTieu = Combobox(self.window, state="readonly")
        self.DSChiTieu['value']=("Shopee","Ăn uống","Mua sắm","Áo quần","Mỹ phẩm","Đi lại","Du lịch","Đổ xăng","Điện thoại","Khác")

        self.Chitieu.place(x=40,y=170)
        self.DSChiTieu.place(x=120,y=172)

        # Số tiền chi tiêu cho sản phẩm
        self.SoTien= Label(master=self.window,text="Số tiền",font=("Arial",10,"bold"))
        self.SoTienEntry= Entry(master=self.window,width=23)

        self.SoTien.place(x=40,y=200)
        self.SoTienEntry.place(x=120,y=202)

        # Các nút bấm
        self.Them = Button(master=self.window, text="Thêm",width=10,command=self.Them_chi_tieu)
        self.CapNhat = Button(master=self.window,text="Cập nhật",width=10,command=self.Cap_nhat_chi_tieu)
        self.Xoa = Button(master=self.window,text="Xóa",width=10,command=self.Xoa_chi_tieu)
        self.Lammoi = Button(master=self.window,text="Làm mới",width=15,command=self.Lam_moi)
        self.ThongKeCTNgay= Button(master=self.window,text="Thống kê chi tiêu ngày",width=37,command=self.Thong_ke_CT_ngay)
        self.ThongKeCTThang= Button(master=self.window,text="Thống kê chi tiêu tháng",width=37,command=self.Thong_ke_chi_tieu_thang)

        self.Them.place(x=40, y =250)
        self.CapNhat.place(x=120,y=250)
        self.Xoa.place(x=200,y=250)
        self.Lammoi.place(x=280, y =250)
        self.ThongKeCTNgay.place(x=40,y = 280)
        self.ThongKeCTThang.place(x=40,y=310)

        # Tổng chi tiêu tháng
        self.TongChiTieuThang = Label(master=self.window,text="TỔNG CHI TIÊU THÁNG: ",font=("Arial",13,"bold"))
        self.TongChiTieuThang.place(x=40,y=343)

        # Tổng trợ cấp tháng
        self.TongTroCapThang= Label(master=self.window,text="TỔNG TRỢ CẤP THÁNG: ",font=("Arial",13,"bold"))
        self.TongTroCapThang.place(x=40,y=370)

        # Phần thống kê chi tiêu trong ngày
        self.DSCTNgay= Label(master=self.window,text="Danh sách chi tiêu trong ngày : ",font=("Arial",10,"bold"))
        self.DSChiTieuTrongNgay = ttk.Treeview(master=self.window,columns=("Name","Price","Bonus"), height=5)
        self.DSChiTieuTrongNgay.bind('<Double-ButtonRelease-1>',self.SelectItemNgay)

        self.DSChiTieuTrongNgay.heading("Name",text="Name")
        self.DSChiTieuTrongNgay.heading("Price",text="Price")
        self.DSChiTieuTrongNgay.heading("Bonus",text="Bonus")
        self.DSChiTieuTrongNgay.column("#0", stretch=NO, minwidth=0, width=0)

        self.DSChiTieuTrongNgay.column("Name",stretch=NO, minwidth=0, width=134)
        self.DSChiTieuTrongNgay.column("Price", stretch=NO, minwidth=0, width=134)
        self.DSChiTieuTrongNgay.column("Bonus",stretch=NO, minwidth=0,width=134)

        self.DSCTNgay.place(x=400,y=60)
        self.DSChiTieuTrongNgay.place(x=400,y=90)

        # Danh sách các chi tiêu trong tháng
        self.DSThang= Label(master=self.window,text="Danh sách chi tiêu trong tháng: ",font=("Arial",10,"bold"))
        self.DSChiTieuTrongThang = ttk.Treeview(master=self.window,columns=("Date","Price","Bonus"), height=5)

        self.DSChiTieuTrongThang.heading("Date",text="Date")
        self.DSChiTieuTrongThang.heading("Price",text="Price")
        self.DSChiTieuTrongThang.heading("Bonus",text="Bonus")

        self.DSChiTieuTrongThang.column("Date",stretch=NO,minwidth=0,width=134)
        self.DSChiTieuTrongThang.column("Price",stretch=NO,minwidth=0,width=134)
        self.DSChiTieuTrongThang.column("Bonus", stretch=NO, minwidth=0, width=134)
        self.DSChiTieuTrongThang.column("#0", stretch=NO, minwidth=0, width=0)

        self.DSThang.place(x=400,y=230)
        self.DSChiTieuTrongThang.place(x=400,y=260)

    def Thong_tin_ngay(self,a):
        self.TrocapEntry.delete(0, END)
        self.DSChiTieu.set("")
        self.SoTienEntry.delete(0, END)
        Ngay = self.DSNgay.get()
        if Ngay != "":
            for i in self.DSChiTieuTrongNgay.get_children():
                self.DSChiTieuTrongNgay.delete(i)
            for j in range(len(self.CTThang)):
                if Ngay == f"{j + 1}":
                    for k in range(len(self.CTThang[j])):
                        self.DSChiTieuTrongNgay.insert('', 'end', values=(self.CTThang[j][k][0],self.CTThang[j][k][1],self.CTThang[j][k][2]))

    def Them_chi_tieu(self):
        SoTien= self.SoTienEntry.get()
        ChiTieu= self.DSChiTieu.get()
        TroCap = self.TrocapEntry.get()
        Ngay = self.DSNgay.get()
        self.DSChiTieuTrongNgay.insert('', 'end', values=(ChiTieu,SoTien,TroCap))
        for i in range(len(self.CTThang)):
            if Ngay == f"{i+1}":
                self.CTThang[i].append([ChiTieu,SoTien,TroCap])

    def Cap_nhat_chi_tieu(self):
        selected = self.DSChiTieuTrongNgay.focus()
        self.DSChiTieuTrongNgay.item(selected,values=(self.DSChiTieu.get(),self.SoTienEntry.get(),self.TrocapEntry.get()))
        Ngay = self.DSNgay.get()

        k = 0
        for i in range(30):
            if f"{i + 1}" == selected[3:]:
                k = i

        for i in range(len(self.CTThang)):
            if Ngay == f"{i+1}":
                self.CTThang[i][k] = [self.DSChiTieu.get(),self.SoTienEntry.get(),self.TrocapEntry.get()]


    def Xoa_chi_tieu(self):
        selected = self.DSChiTieuTrongNgay.focus()
        self.DSChiTieuTrongNgay.delete(selected)

        Ngay = self.DSNgay.get()
        k = 0
        for i in range(30):
            if f"{i + 1}" == selected[3:]:
                k = i

        for i in range(len(self.CTThang)):
            if Ngay == f"{i + 1}":
                self.CTThang[i][k] = []

    def Lam_moi(self):
        self.TrocapEntry.delete(0,END)
        self.DSChiTieu.set("")
        self.SoTienEntry.delete(0,END)

    def Thong_ke_CT_ngay(self):
        Ngay=self.DSNgay.get()
        if len(self.DSChiTieuTrongThang.get_children()) == 0:
            self.DSChiTieuTrongThang.insert('', 'end', values=("Ngày " + Ngay, self.Tong_chi_tieu_ngay(), self.Tong_tro_cap_ngay()))
        else:
            for line in self.DSChiTieuTrongThang.get_children():
                text = self.DSChiTieuTrongThang.item(line)['values'][0]
                if f"{text}" == f"Ngày {Ngay}":
                    self.DSChiTieuTrongThang.item(line, values=("Ngày " + Ngay, self.Tong_chi_tieu_ngay(), self.Tong_tro_cap_ngay()))
                    break
                elif text !="" and f"{text}" != f"Ngày {Ngay}":
                    k=0
                    for lin in self.DSChiTieuTrongThang.get_children():
                        text1 = self.DSChiTieuTrongThang.item(lin)['values'][0]
                        if f"{text1}" != f"Ngày {Ngay}":
                            k=0
                        else:
                            k=lin
                            break
                    if k== 0:
                        self.DSChiTieuTrongThang.insert('', 'end', values=("Ngày " + Ngay, self.Tong_chi_tieu_ngay(), self.Tong_tro_cap_ngay()))
                        break
                    else:
                        self.DSChiTieuTrongThang.item(k, values=("Ngày " + Ngay, self.Tong_chi_tieu_ngay(), self.Tong_tro_cap_ngay()))

    def Tong_chi_tieu_ngay(self):
        self.TongCTNgay = 0
        Ngay = self.DSNgay.get()
        for i in range(len(self.CTThang)):
            if Ngay == f"{i+1}":
                for j in range(len(self.CTThang[i])):
                    self.TongCTNgay += float(self.CTThang[i][j][1])
        return self.TongCTNgay

    def Tong_chi_tieu_thang(self):
        self.TongCTThang =0
        for i in range(len(self.CTThang)):
            for j in range(len(self.CTThang[i])):
                self.TongCTThang += float(self.CTThang[i][j][1])
        self.TongChiTieuThang.configure(text=f"TỔNG CHI TIÊU THÁNG: {round(self.TongCTThang)} VNĐ")
        return self.TongCTThang

    def Tong_tro_cap_ngay(self):
        self.TongTCNgay =0
        Ngay = self.DSNgay.get()
        for i in range(len(self.CTThang)):
            if Ngay == f"{i + 1}":
                for j in range(len(self.CTThang[i])):
                    self.TongTCNgay += float(self.CTThang[i][j][2])
        return self.TongTCNgay

    def Tong_tro_cap_thang(self):
        self.TongTCThang =0
        for i in range(len(self.CTThang)):
            for j in range(len(self.CTThang[i])):
                self.TongTCThang += float(self.CTThang[i][j][2])
        self.TongTroCapThang.configure(text=f"TỔNG TRỢ CẤP THÁNG: {round(self.TongTCThang)} VNĐ")
        return self.TongTCThang

    def Thong_ke_chi_tieu_thang(self):
        ChiTieu= self.Tong_chi_tieu_thang()
        TroCap= self.Tong_tro_cap_thang()

    def SelectItemNgay(self,a):
        selected = self.DSChiTieuTrongNgay.focus()
        Lis = self.DSChiTieuTrongNgay.item(selected)['values']

        self.TrocapEntry.delete(0,END)
        self.TrocapEntry.insert(0,Lis[2])

        self.SoTienEntry.delete(0,END)
        self.SoTienEntry.insert(0,Lis[1])

        for i in range(len(self.DSChiTieu['value'])):
            if self.DSChiTieu['value'][i] == Lis[0]:
                self.DSChiTieu.set(Lis[0])

if __name__ == "__main__":
    app = QuanLyChiTieu()
    app.window.mainloop()
