unit Unit1;

interface

uses
  System.SysUtils, System.Types, System.UITypes, System.Classes, System.Variants,
  FMX.Types, FMX.Controls, FMX.Forms, FMX.Graphics, FMX.Dialogs, System.Rtti,
  FMX.Grid.Style, FMX.Grid, FMX.Controls.Presentation, FMX.ScrollBox,
  FMX.StdCtrls, FMX.Edit;

type
  TForm1 = class(TForm)
    StringGrid1: TStringGrid;
    StringColumn1: TStringColumn;
    StringColumn2: TStringColumn;
    Button1: TButton;
    Button2: TButton;
    Edit1: TEdit;
    procedure Button1Click(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure Button2Click(Sender: TObject);
    procedure StringGrid1DrawColumnCell(Sender: TObject; const Canvas: TCanvas;
      const Column: TColumn; const Bounds: TRectF; const Row: Integer;
      const Value: TValue; const State: TGridDrawStates);
  private
    { Private declarations }
  public
    { Public declarations }
    arr:TArray<Double>;
    elementscol:integer;
  end;

var
  Form1: TForm1;

implementation

{$R *.fmx}

procedure TForm1.Button1Click(Sender: TObject);
var i,j:integer;  sum:double;  temp:double;
begin

  sum:=0;
  SetLength(arr,elementscol);

  for i:=0 to elementscol-1 do
  arr[i]:=Double.Parse(StringGrid1.Cells[0,i]);

  for i:=0 to Length(arr)-1 do
  sum:=sum+arr[i];

  // Сортировка пузырьком
  for i:=1 to Length(arr) do
  begin
    for j:=Length(arr)-1 downto i do
    begin
      if arr[j-1]>arr[j]
       then
      begin
        temp:=arr[j-1];
        arr[j-1]:=arr[j];
        arr[j]:=temp;
      end;
    end;
  end;

  for i:=0 to elementscol-1 do
  begin
    StringGrid1.Cells[1,i]:=arr[i].ToString;
  end;

  Form1.Caption:=sum.ToString;

  ShowMessage('Результат: '+sum.ToString);

end;

procedure TForm1.Button2Click(Sender: TObject);
begin
  elementscol:=integer.Parse(Edit1.Text);
  StringGrid1.RowCount:=elementscol;
end;

procedure TForm1.FormCreate(Sender: TObject);
begin
  elementscol:=integer.Parse(Edit1.Text);
  StringGrid1.RowCount:=elementscol;
end;

procedure TForm1.StringGrid1DrawColumnCell(Sender: TObject;
  const Canvas: TCanvas; const Column: TColumn; const Bounds: TRectF;
  const Row: Integer; const Value: TValue; const State: TGridDrawStates);
var b:TRectF; border:integer;
begin
  b:=bounds;
  border:=1;
 { b.Top:=b.Top+border;
  b.Left:=b.Left-border;
  b.Height:=b.Height-border;
  b.Width:=b.Width-border;   }

  b.Top:=b.Top;
  b.Left:=b.Left;
  b.Height:=b.Height;
  b.Width:=b.Width;

  Canvas.Fill.Color:=TAlphaColorRec.Coral;
  Canvas.FillRect(b,4,4,[TCorner.TopRight,TCorner.BottomRight,TCorner.BottomLeft,TCorner.BottomRight,TCorner.TopLeft],1);
  Canvas.Fill.Color:=TAlphaColorRec.Brown;
  Canvas.Font.Size:=14;
  Canvas.FillText(Bounds,Value.AsString,False,1,[],TTextAlign.Leading);
end;

end.
