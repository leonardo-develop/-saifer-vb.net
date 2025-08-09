Imports System.ComponentModel
Public Class Form1
    Dim settiingshow As Boolean = False
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load

    End Sub

    Private Sub pnlco_Paint(sender As Object, e As PaintEventArgs) Handles pnlco.Paint

    End Sub

    Private Sub txteditor_TextChanged(sender As Object, e As EventArgs)

    End Sub

    Private Sub btnshow_Click(sender As Object, e As EventArgs) Handles btnshow.Click
        If settiingshow = False Then
            pnlco.Visible = False
            btnshow.Text = "show setting"
            settiingshow = True
        Else
            pnlco.Visible = True
            btnshow.Text = "hide setting"
            settiingshow = False
        End If
    End Sub
    Private Sub rbtn_CheckedChanged(sender As Object, e As EventArgs) Handles rbtn.CheckedChanged
        If rbtn.Checked = True Then
            lblcolor.ForeColor = Color.FromArgb(255, 0, 0)
            lbledit.ForeColor = Color.FromArgb(255, 0, 0)
        End If

    End Sub

    Private Sub bbtn_CheckedChanged(sender As Object, e As EventArgs) Handles bbtn.CheckedChanged
        If bbtn.Checked = True Then
            lblcolor.ForeColor = Color.FromArgb(0, 0, 255)
            lbledit.ForeColor = Color.FromArgb(0, 0, 255)
        End If
    End Sub

    Private Sub gbtn_CheckedChanged(sender As Object, e As EventArgs) Handles gbtn.CheckedChanged
        If gbtn.Checked = True Then
            lblcolor.ForeColor = Color.FromArgb(0, 255, 0)
            lbledit.ForeColor = Color.FromArgb(0, 255, 0)
        End If
    End Sub

    Private Sub blbtn_CheckedChanged(sender As Object, e As EventArgs) Handles blbtn.CheckedChanged
        If blbtn.Checked = True Then
            lblcolor.ForeColor = Color.FromArgb(0, 0, 0)
            lbledit.ForeColor = Color.FromArgb(0, 0, 0)
        End If
    End Sub

    Private Sub btncount_Click(sender As Object, e As EventArgs) Handles btncount.Click
        Dim sentence As String = ritext.Text
        Dim words() As String = sentence.Split(" ", StringSplitOptions.RemoveEmptyEntries)
        Dim count As Integer = words.Length()
        MessageBox.Show("Number of words is" & count.ToString())

    End Sub

    Private Sub ExitToolStripMenuItem_Click(sender As Object, e As EventArgs) Handles ExitToolStripMenuItem.Click
        Me.Close()
    End Sub
    Private Sub Form1_Closing(sender As Object, e As CancelEventArgs) Handles Me.Closing
        Dim result As DialogResult = MessageBox.Show("Are you sure you want to close the form?", "Close Form",
       MessageBoxButtons.YesNo, MessageBoxIcon.Question, MessageBoxDefaultButton.Button2)
        If result = DialogResult.No Then
            e.Cancel = True
        End If
    End Sub

    Private Sub btnreplace_Click(sender As Object, e As EventArgs) Handles btnreplace.Click

        If txtfind.Text <> "" Then
            ritext.Text = ritext.Text.Replace(txtfind.Text, txtreplace.Text)
        End If
    End Sub

    Private Sub btnfind_Click(sender As Object, e As EventArgs) Handles btnfind.Click
        Dim searchText As String = txtfind.Text
        Dim startIndex As Integer = 0
        ritext.SelectAll()
        ritext.SelectionBackColor = Color.White

        If searchText <> "" Then
            While startIndex < ritext.TextLength
                Dim wordStartIndex As Integer = ritext.Find(searchText, startIndex, RichTextBoxFinds.None)
                If wordStartIndex <> -1 Then
                    ritext.Select(wordStartIndex, searchText.Length)
                    ritext.SelectionBackColor = Color.Yellow
                    startIndex = wordStartIndex + searchText.Length
                Else
                    Exit While
                End If
            End While
        End If
    End Sub
    Private Sub ritext_TextChanged(sender As Object, e As EventArgs) Handles ritext.TextChanged
    End Sub
End Class
