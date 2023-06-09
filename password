import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class RegistrationProgram {
    private JFrame frame;
    private JLabel label;
    private JButton yesButton;
    private JButton noButton;

    public RegistrationProgram() {
        frame = new JFrame("Программа регистрации");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(300, 150);
        frame.setLayout(new FlowLayout());

        label = new JLabel("Приветствую! Хотите зарегистрироваться в программе?");
        yesButton = new JButton("Да");
        noButton = new JButton("Нет");

        yesButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                showLoginDialog();
            }
        });

        noButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                frame.dispose();
            }
        });

        frame.add(label);
        frame.add(yesButton);
        frame.add(noButton);
        frame.setLocationRelativeTo(null);
        frame.setVisible(true);
    }

    private void showLoginDialog() {
        JDialog dialog = new JDialog(frame, "Регистрация: введите логин", true);
        dialog.setLayout(new FlowLayout());

        JLabel loginLabel = new JLabel("Логин:");
        JTextField loginField = new JTextField(10);
        JButton okButton = new JButton("OK");

        okButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String login = loginField.getText();
                if (isValidLogin(login)) {
                    dialog.dispose();
                    showPasswordDialog();
                } else {
                    JOptionPane.showMessageDialog(dialog, "Неверный логин. Логин должен быть больше 5 символов и не содержать пробелов.", "Ошибка", JOptionPane.ERROR_MESSAGE);
                }
            }
        });

        dialog.add(loginLabel);
        dialog.add(loginField);
        dialog.add(okButton);
        dialog.pack();
        dialog.setLocationRelativeTo(frame);
        dialog.setVisible(true);
    }

    private void showPasswordDialog() {
        JDialog dialog = new JDialog(frame, "Регистрация: введите пароль", true);
        dialog.setLayout(new FlowLayout());

        JLabel passwordLabel = new JLabel("Пароль:");
        JPasswordField passwordField = new JPasswordField(10);
        JButton okButton = new JButton("OK");

        okButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                char[] passwordChars = passwordField.getPassword();
                String password = new String(passwordChars);

                if (isValidPassword(password)) {
                    dialog.dispose();
                    showConfirmPasswordDialog(password);
                } else {
                    JOptionPane.showMessageDialog(dialog, "Неверный пароль. Пароль должен быть больше 8 символов, не содержать пробелов и должен содержать хотя бы одну цифру и хотя бы одну букву.", "Ошибка", JOptionPane.ERROR_MESSAGE);
                }
            }
        });

        dialog.add(passwordLabel);
        dialog.add(passwordField);
        dialog.add(okButton);
        dialog.pack();
        dialog.setLocationRelativeTo(frame);
        dialog.setVisible(true);
    }

    private void showConfirmPasswordDialog(String originalPassword) {
        JDialog dialog = new JDialog(frame, "Регистрация: подтвердите пароль", true);
        dialog.setLayout(new FlowLayout());

        JLabel confirmPasswordLabel = new JLabel("Повторите пароль:");
        JPasswordField confirmPasswordField = new JPasswordField(10);
        JButton okButton = new JButton("OK");

        okButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                char[] confirmPasswordChars = confirmPasswordField.getPassword();
                String confirmPassword = new String(confirmPasswordChars);

                if (confirmPassword.equals(originalPassword)) {
                    dialog.dispose();
                    showRegistrationSuccessDialog();
                } else {
                    JOptionPane.showMessageDialog(dialog, "Пароли не совпадают. Повторите ввод.", "Ошибка", JOptionPane.ERROR_MESSAGE);
                }
            }
        });

        dialog.add(confirmPasswordLabel);
        dialog.add(confirmPasswordField);
        dialog.add(okButton);
        dialog.pack();
        dialog.setLocationRelativeTo(frame);
        dialog.setVisible(true);
    }

    private void showRegistrationSuccessDialog() {
        JOptionPane.showMessageDialog(frame, "Регистрация успешно завершена!", "Успех", JOptionPane.INFORMATION_MESSAGE);
    }

    private boolean isValidLogin(String login) {
        return login.length() > 5 && !login.contains(" ");
    }

    private boolean isValidPassword(String password) {
        return password.length() > 8 && !password.contains(" ") && password.matches(".*\\d.*") && password.matches(".*[a-zA-Z].*");
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new RegistrationProgram();
            }
        });
    }
}
